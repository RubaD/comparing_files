# comparing files with Ansible
There is two playbooks :
- **copy.yml** which is used to copy files from remote hosts to the localho
- **loop.yml**   which used to compare different files.


### how it works
- **copy.yml** : at first it creates a directory with the host name in the desired location to copy the files there , after that it includes the file that containes the pathes of the files that will be copied, then it uses fetch module to copy these files.
- **loop.yml** : fisrt two lists are created to store any chnages between the files, then the compare.yml which has the tasks the compare the files is included, in compare.yml template module was used with dry run and diff to collect the needed data about the files ( checksum , selinux , owner and group) these data was compared and if there is any change, these chnages will be added to the lists , in case there is a content change copy module with dry run and diff was used to display the difference. 
### How to use 
- **copy.yml** takes location variable as an arguemnt and it is where to copy the files.
- **loop.yml** takes two varibale: first_dir , sec_dir as arguments and these where are the files that will be compared.
