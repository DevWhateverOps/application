# GitHub Actions Template

This action prints and returns a salutation.

The metadata file `action.yml` and `README.md` can be used as a template/reference for new 

## Inputs

### `who-to-greet`

**Required** The name of the person to greet. Default `"World"`.

## Outputs

### `salutation`

The generated salutation.

## Example usage

```yaml
- name: Checkout shared repo
  uses: actions/checkout@v2
  with:
    repository: vwdfive/shared-actions
    token: ${{ secrets.PAT }}
    path: shared-actions
    ref: develop

- uses: ./shared-actions/action-template
  with:
    who-to-greet: 'Developer'
```
