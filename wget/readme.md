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
#### ![image](https://github.com/Shin-jongwhan/microsoft_onedrive/assets/62974484/9375de5d-4f45-43e7-9ed9-7424f66ccea4)
### <br/>


