---
tags: [Development/GitHub/Actions]
title: Run only on a tagged commit
created: '2022-01-03T09:22:41.040Z'
modified: '2022-01-03T09:23:06.868Z'
---

# Run only on a tagged commit

* https://packaging.python.org/en/latest/guides/publishing-package-distribution-releases-using-github-actions-ci-cd-workflows/#publishing-the-distribution-to-pypi-and-testpypi
```yaml
    - name: Publish distribution 📦 to PyPI
      if: startsWith(github.ref, 'refs/tags')
      uses: pypa/gh-action-pypi-publish@master
      with:
        password: ${{ secrets.PYPI_API_TOKEN }}
```
