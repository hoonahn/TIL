# ssh

## scp

> server to server file transfer

1. Remote server to Local server

```bash
scp [option] [username]@[remote_server_ip]:[directory_of_file] [local_directory_to_recieve]
# Example
scp abc@111.222.333.444:/home/abc/a.py /home/usr/python_project/
```

2. Local server to Remote server

```bash
scp [option] [local_directory_of_file] [username]@[remote_server_ip]:[directory_to_recieve] 
# Example
scp /home/usr/python_project/a.py abc@111.222.333.444:/home/abc/
```

3. Server with port options

```bash
# Server using 2222 ssh port
# -P option means port number
scp -P 2222 /home/usr/python_project/a.py abc@111.222.333.444:/home/abc/
```

- Some options
  - -P: Port number
  - -p: Preserve the mod and modified/ued date of the original file
  - -r: Copy all the child directory and files

---

#### Reference

- [scp 명령어를 이용한 파일 복사 및 전송](http://faq.hostway.co.kr/?mid=Linux_ETC&page=8&document_srl=1426)