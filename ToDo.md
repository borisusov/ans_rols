# To Do List
    1.1 Read about Maven Goal lifecycles:
    https://maven.apache.org/guides/introduction/introduction-to-the-lifecycle.html

    2 save artifact  *.war in Jenkins if job is successfull
    3 web hook after commit. Jenkins must check repo for changes onse per min 
    3.1  target - Each new commit to the code must trigg jenkins job
4 install artifactory jfrog and setup repo for maven (web interface)
5 maven 

## artifactory

- [X]  add artifactory bin folder to the PATH variable
- [ ] howto set env var permanently

  ```bash
  export JFROG_HOME=<full path of the jfrog directory>
  ```

* add systemd unit for artifactory

## vscode

 - [ ] при выделении в консоли текста автоматически copy

## laptop

- [X] install oh my zsh default shell in console
- [ ] install clipit with hot keys - renew

## jenkins
* add build description with artifact version
> add git tags with artifact version

* version from pom.xml

## examples

1. First item
2. Second item
    - one word
        > mysl

    - two words
       > mysl 1
3. Third item


## markdown
- [X] format to read

## jenkins plugin
* pipeline-utility-steps -plugin for parse pom.xml
* working script

``` 
script {
    pom = readMavenPom file: 'pom.xml'
    echo pom.project.version
}

```


