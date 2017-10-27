# spring-social-naver
Spring Social Project for login API provided by NAVER

네이버 아이디로 로그인 OpenAPI 개발 가이드를 참고하여 작성되었습니다.
https://nid.naver.com/devcenter/docs.nhn?menu=API

### v1.0.0 (2015.09.21)
---
- 코드 신규 등록
- 네이버 아이디로 로그인 기능

### maven으로 변경 (2017.10.27)
---
jcenter에 링크를 대행해주는 bintray에 업로드하기 위해 maven으로 변경.  

모든 설명은 mac os 기준으로 설명하겠다.  
bintray에 업로드 하기 위해서는 우선 maven을 설치해야한다.  
brew로 설치하는 게 가장 간편한 것 같다.  
```bash
brew update
brew install maven
```

bintray의 api키를 프로젝트 디렉토리에 넣으면 깃헙에 올라 갈 위험이 있다.  
그리고 아래 디렉토리에 settings.xml을 만들자.  
```bash
touch ~/.m2/settings.xml
```

아래 내용을 복붙하자.  
```xml
<?xml version="1.0" encoding="UTF-8"?>
<settings
        xsi:schemaLocation="http://maven.apache.org/SETTINGS/1.0.0 http://maven.apache.org/xsd/settings-1.0.0.xsd"
        xmlns="http://maven.apache.org/SETTINGS/1.0.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">
    <servers>
        <!-- server 부분은 bintray에 맞게 수정해야한다. -->
        <server>
            <id>lib_name</id>
            <username>user_name</username>
            <password>api_key</password>
        </server>
    </servers>
    <profiles>
        <profile>
            <repositories>
                <repository>
                    <snapshots>
                        <enabled>false</enabled>
                    </snapshots>
                    <id>central</id>
                    <name>bintray</name>
                    <url>http://jcenter.bintray.com</url>
                </repository>
            </repositories>
            <pluginRepositories>
                <pluginRepository>
                    <snapshots>
                        <enabled>false</enabled>
                    </snapshots>
                    <id>central</id>
                    <name>bintray-plugins</name>
                    <url>http://jcenter.bintray.com</url>
                </pluginRepository>
            </pluginRepositories>
            <id>bintray</id>
        </profile>
    </profiles>
    <activeProfiles>
        <activeProfile>bintray</activeProfile>
    </activeProfiles>
</settings>
```

bintray에 deploy 하려면 아래 명령어를 실행하자.  
```bash
mvn clean deploy
```

### License
---
MIT
