### 240111
## wget 으로 onedrive 파일 받는 방법
### 먼저 공유 설정에 파일 공유 누르고 공유 설정에서 엑세스 권한을 누구나로 설정한 후 링크 생성을 클릭한다.
#### ![image](https://github.com/Shin-jongwhan/microsoft_onedrive/assets/62974484/55e14a12-0100-410f-b5dd-785a60a77c6f)
#### ![image](https://github.com/Shin-jongwhan/microsoft_onedrive/assets/62974484/26e3b549-1aee-4168-bc4d-4b936cc98cee)
### <br/>

### wget 으로 파일을 다운로드하려면 링크 복사를 눌러서 나온 주소 뒤에 &download=1 만 붙여주면 다운로드할 수 있다고 한다.
```
wget -O test.txt "https://theragenbio365-my.sharepoint.com/:t:/g/personal/jonghwan_shin_theragenbio_com/EdR82mqGw69Dn0nPupOLfDcBaRRYq2wqFDmN5hhUNK8AbQ?e=bOgMfR&download=1"
```
### 다운로드가 잘 된다.
### 근데 이 방법은 expired date 가 설정이 되어 있는 것이라서 해결책은 못 된다.
#### ![image](https://github.com/Shin-jongwhan/microsoft_onedrive/assets/62974484/9375de5d-4f45-43e7-9ed9-7424f66ccea4)
### <br/>


## 리눅스에 onedrive 연결 방법
### 아래 블로그를 참고하였다.
### https://velog.io/@openjr/%EC%9A%B0%EB%B6%84%ED%88%AC-Onedrive-%EC%84%A4%EC%B9%98
### <br/>

### config 를 복사
```
cp config ~/.config/onedrive/config
```

### config 를 복사하고 나서 다음과 같이 수정하였다.
### 기능하게 하려면 주석 처리를 지워야 한다.
```
# Configuration for OneDrive Linux Client
# This file contains the list of supported configuration fields
# with their default values.
# All values need to be enclosed in quotes
# When changing a config option below, remove the '#' from the start of the line
# For explanations of all config options below see docs/USAGE.md or the man page.
#
sync_dir = "/data/data/onedrive"
# skip_file = "~*|.~*|*.tmp"
# monitor_interval = "300"
skip_dir = "바탕 화면|앱|첨부 파일|사진"
# log_dir = "/var/log/onedrive/"
# drive_id = ""
# upload_only = "false"

...
```
### <br/>

### 그러면 다음과 같이 폴더가 동기화된다.
#### ![image](https://github.com/Shin-jongwhan/microsoft_onedrive/assets/62974484/a992cee8-826e-4552-aacd-6e5465ac27b5)
### <br/><br/><br/>

## business shared folder 받는 방법
### 먼저 config 를 수정해야 한다.
### 여기서 필요한 건 sync_business_shared_folders 이다.
```
sync_dir = "/data/data/onedrive_shared"
skip_dir = "바탕 화면|앱|첨부 파일|사진|Microsoft Teams 채팅 파일|문서|그림"
skip_symlinks = "false"
sync_business_shared_folders = "true"
```
