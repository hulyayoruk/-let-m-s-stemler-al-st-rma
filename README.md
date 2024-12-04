

İLK ALIŞTIRMA:

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


 İKİNCİ ALIŞTIRMA:
 
