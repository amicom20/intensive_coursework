# script.md

##training 계정 생성 및 그룹추가(all server)
```
sudo useradd training 
sudo passwd training  /  training
sudo usermod -aG wheel training
```

## filezilla 를 통해 파일 업로드 
```
all.zip 압축 풀면 training_materials 폴더가 있음.
cm이 있는 노드와 데이터노드(nd1번, nd3번)에 training_materials 를 /home/training/ 에 업로드
```

## nd1 에서 db 실행 후 training 계정 생성
```
mysql -u root -p
비밀번호 : password 입력

GRANT ALL ON *.* TO 'training'@'%' IDENTIFIED BY 'training';
FLUSH PRIVILEGES;
EXIT;		
```

## nd1, nd3 에서 /home/training/training_materials/devsh/scripts/setup.sh 수행
```
setup.sh 실행 권한 없을 경우
chmod 766 setup.sh 수행
```











