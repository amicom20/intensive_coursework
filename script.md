##  1. Installing Kafka requires some special attention. You will need to download, distribute and activate the Kafka package before you can add the Kafka service.
```
CM -> 우측 상단 패키지 아이콘 클릭 -> Kafka service 설치
```

##  2. Create user “training” with password “training” and add to group wheel for sudo access.
```
1) training 계정 생성
	sudo useradd training 
2) training 계정 패스워드 설정
	sudo passwd training
	-> 비밀번호 training 으로 설정
3) 사용자 그룹 추가
	training sudo usermod -aG wheel training
```

##  3. Log into Hue as user “training” with password “training”
```
Hue -> 웹 UI 접속 -> training / training 접속
```

##  4. From the bit.ly folder, download all.zip and unzip it. 4-1) Do this in both your CM host and one of the datanode hosts. 
```
filezilla 를 통해 파일 업로드
all.zip 압축 풀면 training_materials 폴더가 있음.
cm이 있는 노드와 데이터노드(nd1번, nd3번)에 training_materials 를 /home/training/ 에 업로드
```

##   4-2) Go to training_material/devsh/scripts and review the setup.sh See how it works. We are going to use it to create some data for ourselves but it won’t work right away. See if you can figure out what needs to be done to make it work.
```
	nd1, nd3 에서 /home/training/training_materials/devsh/scripts/setup.sh 수행
setup.sh 실행 권한 없을 경우
chmod 766 setup.sh 수행
```	
##  You will need to add user “training” with password “training” to your MySql installation and Grant the necessary rights
```
nd1 에서 db 실행 후 training 계정 생성
mysql -u root -p
비밀번호 : password 입력

GRANT ALL ON *.* TO 'training'@'%' IDENTIFIED BY 'training';
FLUSH PRIVILEGES;
EXIT;	
```  
