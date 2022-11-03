---
tags: [Python, Python/Logging]
title: Logging
created: '2022-10-28T09:49:59.547Z'
modified: '2022-11-03T01:52:06.689Z'
---

# Logging

```python
default_factory = logging.getLogRecordFactory()

def record_factory(*args, **kwargs):
    record = default_factory(*args, **kwargs)
    record.location = f"{record.funcName:s}:{record.lineno:d}"
    return record

logging.setLogRecordFactory(record_factory)


class AccessLogFilter(logging.Filter):
    def filter(self, record: logging.LogRecord) -> int:
        """Log record if filter returns True"""
        return record.name != "uvicorn.access"


root_logger = logging.getLogger()
root_logger.setLevel(logging.CRITICAL)
root_logger.addHandler(logging.NullHandler())


def get_logger(name, *, level=logging.INFO) -> logging.Logger:
    logger = logging.getLogger(name)
    logger.setLevel(level)
    handler = logging.StreamHandler()
    # https://docs.python.org/3/library/logging.html#logrecord-attributes
    formatter = logging.Formatter(
        style="{",
        fmt="{asctime:s} | {levelname: <9s} | {name: <20s} | {location: <25s} | {message:s}",
        datefmt="%Y-%m-%d %H:%M:%S",
    )
    handler.setFormatter(formatter)
    logger.addHandler(handler)
    return logger
```

### `uvicorn`

```yaml
version: 1
disable_existing_loggers: False

formatters:
  default:
    (): 'uvicorn.logging.DefaultFormatter'
    fmt: '%(asctime)s | %(levelname)-9s | %(name)-20s | %(location)-25s | %(message)s'
    datefmt: "%Y-%m-%d %H:%M:%S"
  access:
    (): 'uvicorn.logging.AccessFormatter'
    fmt: '%(asctime)s | %(levelname)-9s | %(name)-20s | %(client_addr)-25s | %(status_code)s | "%(request_line)s"'
    datefmt: "%Y-%m-%d %H:%M:%S"

filters:
  access_log:
    (): 'utils.AccessLogFilter'

handlers:
  default:
    class: logging.StreamHandler
    formatter: default
    stream: ext://sys.stdout
    filters: [access_log]
  access:
    class: logging.StreamHandler
    formatter: access
    stream: ext://sys.stdout

loggers:
  uvicorn:
    level: INFO
    # propagate: False
    handlers:
      - default
  uvicorn.error:
    level: INFO
  uvicorn.access:
    level: INFO
    handlers:
      - access
```
