---
layout: post
title: "슈퍼푸티로 AWS EC2 인스턴스 접속 방법"
date: 2020-06-14 22:43:46
categories: putty
tag: putty
comments:
---
> ##### ppk 파일 생성
1. puttygen 을 이용하여 pem 파일 ppk 파일로 변경([puttygen 없을경우 설치](https://www.puttygen.com/#Download_PuTTYgen_on_Windows))  
 - puttygen > Load > pem 파일 선택 > Save private key 클릭하여 ppk 파일 저장  
<img src="https://drive.google.com/uc?export=download&id=1pnGTf7IswW67AmvOtaWD-wHcNPKrKN_B"/>  
  
> ##### superPutty 에서 설정  
1. superPutty > Tools > Putty Configuration  
<img src="https://drive.google.com/uc?export=download&id=1yzHVFI_GROF2W1KxqmF4CIbIarpXHP_p"/>  
2. AWS EC2 인스턴스의 외부 IP주소를 적음  
 - centos 의 경우 계정이 centos 로 생성되므로 centos@IP주소 로 표기한다.  
<img src="https://drive.google.com/uc?export=download&id=1Vje4e316e0lkaAGV9WDS-JxStA47Uuk4"/>  
3. 좌측 Connection > SSH > Auth 에서 처음에 생성한 ppk 파일을 로드해줌  
<img src="https://drive.google.com/uc?export=download&id=1SRZpp21pVLsYsLEcCVVWAWT7k35E-Rks"/>  
4. 위에서 설정된 내용을 save 한다.  
<img src="https://drive.google.com/uc?export=download&id=10IKSaD7GCU-14dnm6I9RFUKQCvEA6L9p"/>  
  
> ##### 슈퍼푸티에서 바로 접속할 수 있도록 접속정보 추가  
1. 푸티에 설정된 정보를 슈퍼푸티로 임포트 한다.  
2. 슈퍼푸티 우측 세션들에서 확인 가능.  
<img src="https://drive.google.com/uc?export=download&id=1XM5NFRucleIT9MauxHrF8-3jt8J0KmZS"/>  

