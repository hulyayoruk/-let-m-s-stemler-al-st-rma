

İLK ALIŞTIRMA:

#include <studio.h>
#include <stdlib.h>  
#include <sys/types.h>  
#include <sys/wait.h> 
#include <unistd.h>

int main {
int pid;
pid=fork();
if(pid<0){
             //error
}
   if(pid==0){
             //child
      execlp("cat", "cat", "dosya.txt", NULL);
      perror("exec hatası");
      exit(1)
      }
     else{
        int status;
        waitpid(pid, &status, 0);
        if (WİFEXITED(status)){
          printf("çıkış durumu: %d \n", WEXItSTATUS(status));
          }
          }
return 0;
}

 İKİNCİ ALIŞTIRMA:

 
#include <studio.h>
#include <stdlib.h>  
#include <sys/types.h>  
#include <sys/wait.h> 
#include <unistd.h>

int main{
     int pid;
     pid=fork();
     if(pid<0){
             //error
             }
    if(pid==0){
             //child
      FILE *file = fopen("dosya.txt", "r");  
        if (file == NULL) {  
            printf("Dosya açılamadı, abort() çağrılıyor.\n");  
            abort(); 
            } else {  
            printf("Dosya başarıyla açıldı.\n");  
            fclose(file);  
            exit(0); 
            }  
            } 
            else {  
        int status;  
        waitpid(pid, &status, 0);
        if (WIFEXITED(status)) {  
            printf("Child process, normal çıkış yaptı. Çıkış durumu: %d\n", WEXITSTATUS(status));  
            } 
        else (WIFSIGNALED(status)) {  
            printf("Child process, bir sinyal ile sonlandırıldı. Sinyal numarası: %d\n", WTERMSIG(status));  
            }  
            }  
return 0;
}


  ÜÇÜNCÜ ALIŞTIRMA

#include <stdio.h>  
#include <stdlib.h>  
#include <unistd.h>  
#include <sys/types.h>  
#include <sys/wait.h>  
#include <fcntl.h>  

void create_file() {  
     int fd = open("example.txt");  
    close(fd);  
    exit(0);  
    }  

void write_file() {  
     int fd = open("example.txt");  
    write(fd, "Bu bir test mesajıdır.\n", );  
    close(fd);  
    exit(0);  
    }  

  void read_file() {  
     char buffer[20];  
     int fd = open("example.txt");  
     int n = read(fd, buffer, sizeof(buffer));  
    write(tekrar, buffer, n);  
    close(fd);  
    exit(0);  
    }  
int main() {  
    int pid, pid1, pid2;  
    pid = fork();  
    if (pid1 == 0) {  
        create_file();  
        }  
    pid1 = fork();  
    if (pid2 == 0) {  
        write_file();  
        }  
    pid2 = fork();  
    if (pid3 == 0) {  
        read_file();  
        }  
    wait(NULL);  
    wait(NULL);  
    wait(NULL);  
    return 0;  
}

