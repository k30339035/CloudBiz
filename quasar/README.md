```
mkdir myproject && cd "$_"
docker run --rm -v ${PWD}:/app -it node:13.14-alpine sh -c "yarn global add @vue/cli && vue init 'quasarframework/quasar-starter-kit' app"


docker build -t dockerize-quasar .
```