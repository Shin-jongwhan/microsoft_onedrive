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
### <br/>

### 공유 폴더 리스트 확인
```
./onedrive --list-shared-folders
```
#### ![image](https://github.com/Shin-jongwhan/microsoft_onedrive/assets/62974484/8a5f57fa-104c-44a6-93b5-2a7d5a579d7c)
### <br/>

### 그 다음 \[config dir\]/business_shared_folders 파일을 만들어 편집한다.
### 여기에 적은 폴더 이름이 가져올 폴더이다.
```
vi ~/.config/onedrive/business_shared_folders
```

```
# comment
2023 한국인칩 분석 교육을 위한 워크샵
jhshin_test
# Another comment
#Top Level to Share
```
### <br/>

### config 설정 확인
```
[onedrive_path]/onedrive --confdir ~/.config/onedrive_shared/ --display-config
```

```
Configuration file successfully loaded
onedrive version                             = v2.4.25-13-g1a88d33
Config path                                  = /home/jhshin/.config/onedrive_shared/
Config file found in config path             = true
Config option 'sync_dir'                     = /data/data/onedrive_shared
Config option 'enable_logging'               = false
Config option 'log_dir'                      = /var/log/onedrive/
Config option 'disable_notifications'        = false
Config option 'min_notify_changes'           = 5
Config option 'skip_dir'                     = 바탕 화면|앱|첨부 파일|사진|Microsoft Teams 채팅 파일|문서|그림
Config option 'skip_dir_strict_match'        = false
Config option 'skip_file'                    = ~*|.~*|*.tmp
Config option 'skip_dotfiles'                = false
Config option 'skip_symlinks'                = false
Config option 'monitor_interval'             = 300
Config option 'monitor_log_frequency'        = 6
Config option 'monitor_fullscan_frequency'   = 12
Config option 'read_only_auth_scope'         = false
Config option 'dry_run'                      = false
Config option 'upload_only'                  = false
Config option 'download_only'                = false
Config option 'local_first'                  = false
Config option 'check_nosync'                 = false
Config option 'check_nomount'                = false
Config option 'resync'                       = false
Config option 'resync_auth'                  = false
Config option 'cleanup_local_files'          = false
Config option 'classify_as_big_delete'       = 1000
Config option 'disable_upload_validation'    = false
Config option 'bypass_data_preservation'     = false
Config option 'no_remote_delete'             = false
Config option 'remove_source_files'          = false
Config option 'sync_dir_permissions'         = 700
Config option 'sync_file_permissions'        = 600
Config option 'space_reservation'            = 52428800
Config option 'application_id'               =
Config option 'azure_ad_endpoint'            =
Config option 'azure_tenant_id'              = common
Config option 'user_agent'                   =
Config option 'force_http_11'                = false
Config option 'debug_https'                  = false
Config option 'rate_limit'                   = 0
Config option 'operation_timeout'            = 3600
Config option 'dns_timeout'                  = 60
Config option 'connect_timeout'              = 10
Config option 'data_timeout'                 = 600
Config option 'ip_protocol_version'          = 0
Config option 'sync_root_files'              = false
Selective sync 'sync_list' configured        = false
Config option 'sync_business_shared_folders' = true
Business Shared Folders configured           = true
business_shared_folders contents:
# comment
2023 한국인칩 분석 교육을 위한 워크샵
jhshin_test
# Another comment
#Top Level to Share
Config option 'webhook_enabled'              = false
```
### <br/>

### sync 요청
```
[onedrive_path]/onedrive --synchronize --resync --sync-shared-folders --verbose --confdir ~/.config/onedrive_shared/
```
### <br/>

### 특정 폴더에 있는 폴더 또는 파일 다운로드만 하기
```
[onedrive_path]/onedrive --synchronize --resync --sync-shared-folders --verbose --confdir ~/.config/onedrive_shared/ --single-directory SinlgeCellRunInfo/ --download-only --disable-download-validation
```
### 그런데 이렇게 하면 로컬에 있는 파일을 복사본으로 만든다.
#### ![image](https://github.com/Shin-jongwhan/microsoft_onedrive/assets/62974484/98a2f7f8-9d0a-4d04-928a-9569eddacc8e)
### --cleanup-local-files 옵션을 쓰면 복사본은 안 생기고 onedrive 파일 복사만 가능하게 할 수 있다.
#### ![image](https://github.com/Shin-jongwhan/microsoft_onedrive/assets/62974484/3bc98b1b-471a-43dd-a717-ef006dc39b9d)
### <br/>

### sync 되었는지 확인
### shared folder 가 잘 가져와졌다.
#### ![image](https://github.com/Shin-jongwhan/microsoft_onedrive/assets/62974484/b16876c6-2ef9-4b11-8399-63851e711aab)
### <br/><br/><br/>

## 옵션
- --single-directory \[path\] : config 에 있는 sync_dir 는 제외하고 path 를 적는다.
- --upload-only : server -> onedrive 로 업로드
- --download-only : onedrive -> server 로 다운로드
- --disable-download-validation : download 할 때 validation 을 해제한다.
- --disable-upload-validation : upload 할 때 validation 을 해제한다.
- --cleanup-local-files : --download-only 옵션을 사용할 때, 복사본이 생기는데 안 만들게 한다.
