# Deploy React App To Github Pages

This github action builds your react app and assuming it is build in the build directory deploys it to the branch gh-pages

## Example 

```name: Deploy Code
on:
  push:
    branches: [ master ]

jobs:
  build:
    runs-on: ubuntu-latest

    steps:
    - uses: actions/checkout@v2
    - name: Setup Node
      uses: actions/setup-node@v1
      with:
        node-version: '10.x'
    - name: Run npm install
      run: npm install
    - name: Build Code
      run: |
        echo Building code,
        npm run-script build
    - name: Deploy
      uses: JamesIves/github-pages-deploy-action@3.5.9
      with:
        GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
        BRANCH: gh-pages 
        FOLDER: build #

```

## Contributing
Pull requests are welcome. For major changes, please open an issue first to discuss what you would like to change.

Please make sure to update tests as appropriate.

## License
[MIT](https://choosealicense.com/licenses/mit/)