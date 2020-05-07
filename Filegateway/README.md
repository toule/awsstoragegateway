# Storage Gateway - File Gateway

![inital](images/inital.png)

## NFS

### Select Gateway

![selectgateway](images/selectgateway.png)



### Select Host platform

![hosttype](images/hosttype.png)

- 주의점
  - 인스턴스는 xlarge 이상으로 하는 것을 권장함 (vCPUs 4이상, Memory 16이상, 캐시용 EBS는 150이상)

![AMI](images/ami.png)

- 기생성된 Storage Gateway Image를 사용하며 m5a.xlarge를 사용
- 인스턴스는 public subnet에 구성
- Tag는 Name:NFS-Storage-Gateway로 생성
- Elastic IP를 만들어서 Attach하는 것을 권장함
- 나머지는 Default

### Select Storage

![disk](images/disk.png)

### Security Group

![sg](images/sg.png)

- 테스트용으로 모두 Any로 구성

- 참고: 포트 요구사항 (https://docs.aws.amazon.com/ko_kr/storagegateway/latest/userguide/Resource_Ports.html)

![port](images/port.png)

443(HTTPS) : AWS Service Endpoint

80(HTTP) : 정품 인증 전용, Storage Gateway 어플라이언스의 정품 인증 동안에만 사용

53(DNS) : Storage Gateway VM과 DNS 서버 간의 통신

22(TCP) : 지원 채널

123(NTP) : 로컬 시스템이 VM 시간을 호스트 시간과 동기화 하는데 사용

NFS(111, 2049, 20048) : 파일 공유 데이터 전송



### Select Endpoint

![endpoint](images/endpoint.png)

- 테스트용으로 Public하게 구성



### Connect Gateway

![connect](images/connect.png)



### Active

![active](images/active.png)



### Configure local disks (Cache Storage)

![localdisk](images/localdisk.png)



### Log Group

![loggroup](images/loggroup.png)



### Confirm Gateway

![gateway](images/gateway.png)



### File share (Connect S3)

![fileshare](images/fileshare.png)

![setting-fileshare](images/setting-fileshare.png)

![stores3](images/stores3.png)



### Confirm File share

![confirm-fileshare](images/confirm-fileshare.png)



### Test

#### SSH Admin Connection

![admin](images/admin.png)

#### Windows

![windows-mount](images/windows-mount.png)

![windows-result](images/windows-result.png)



#### Linux

![linux-result](images/linux-result.png)