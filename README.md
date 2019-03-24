# Kullanici-Etkilesimli-Karne-Uygulamasi

// Öğrenci sayısını, ortalamalarını ve başarı sıralamalarını gösteren kullanıcılı etkileşimli C programı




    int main(){
    int AA=0, BB=0, CC=0, DD=0, FF=0, index, index2;
    int selection, i, a, count, min, max;
    double ort, toplam;
    char lettermax, lettermin;
    srand(40);
    /* 3 ile 50 arasinda sayi girilmediyse tekrar sormasi icin do-while dongusu */
    do{
        printf("Enter student count: ");
        scanf("%d", &count);
        if(count < 3 || count > 50){
            printf("Not in Range!!!\n");
        }
    }while(count < 3 || count > 50);
    /* en basarili ve basarisiz ogrenci notunu kaydetmek icin tanimlanan degiskenler */
    min = 99;
    max = 0;
    toplam = 0;
    
    for(i = 1; i <= count; i++){
        a = rand()%100;
        /*Her harf notunun kacar kere kullanildigini hesaplamak icin kullanilan if-else if ler */
        if(a <= 100 && a >= 90){
            AA = AA + 1;
        }
        else if(a <= 89 && a >= 80){
            BB = BB + 1;
        }
        else if(a <= 79 && a >= 70){
            CC = CC + 1;
        }
        else if(a <= 69 && a >= 60){
            DD = DD + 1;
        }
        else if(a <= 59 && a >= 0){
            FF = FF + 1;
        }
        printf("%2d ", a);
        if(i % 15 == 0){    /* <----Ogrenci notlarinin daha duzenli gosterilmesi icin yazildi */
            printf("\n");
        }
        /* En basarisiz ogrenci notunu hesaplamak icin kullanilan dongu */
        if(a < min){
            min = a;
            index = i;   /*<----Kacinci notun en basarisiz oldugunu bulmak icin yapilan atama */
            /*Notun harf degerini bulma */
            if(min >= 90 && min <= 100){
                lettermin = 'A';
            }
            else if(min >= 80 && min <= 89){
                lettermin = 'B';
            }
            else if(min >= 70 && min <= 79){
                lettermin = 'C';
            }
            else if(min >= 60 && min <= 69){
                lettermin = 'D';
            }
            else if(min >= 0 && min <= 59){
                lettermin = 'F';
            }
        }
        /*En basarili ogrenci icin kullanilan dongu */
        if(a > max){
            max = a;
            index2 = i;
            if(max >= 90 && max <= 100){
                lettermax = 'A';
            }
            else if(max >= 80 && max <= 89){
                lettermax = 'B';
            }
            else if(max >= 70 && max <= 79){
                lettermax = 'C';
            }
            else if(max >= 60 && max <= 69){
                lettermax = 'D';
            }
            else if(max >= 0 && max <= 59){
                lettermax = 'F';
            }
        }
        toplam = a + toplam;
        ort = toplam / i;
    }
    /* Menunun surekli gosterilmesi icin kullanilan do while dongusu */
    do{
        printf("\n---------------------------------------------\n");
        printf("Student Score Calculator Menu for %d Student\n", (i-1));
        printf("1) Most Succesful Student\n");
        printf("2) Most unsuccesful Student\n");
        printf("3) Letter Grade Statistics\n");
        printf("4) Calculate Avarage\n");
        printf("5) Show all Data\n");
        printf("                        Make Selection: ");
        scanf("%d", &selection);
        switch(selection){
            case 1:
                printf("Most Succesful student:\n");
                printf("Index: %d\n", index2);
                printf("Score: %d\n", max);
                printf("Letter grade: %c\n", lettermax);
                break;
            case 2:
                printf("Most unsuccesful student:\n");
                printf("Index: %d\n", index);
                printf("Score: %d\n", min);
                printf("Letter grade: %c\n", lettermin);
                break;
            case 3:
                printf("%2d student got letter grade 'A'\n", AA);
                printf("%2d student got letter grade 'B'\n", BB);
                printf("%2d student got letter grade 'C'\n", CC);
                printf("%2d student got letter grade 'D'\n", DD);
                printf("%2d student got letter grade 'F'\n", FF);
                break;
            case 4:
                printf("\nThe average Score of %d Student is %.2lf\n", (i-1), ort);
                break;
            case 5:
                printf("Most Succesful student:\n");
                printf("Index: %d\n", index2);
                printf("Score: %d\n", max);
                printf("Letter grade: %c\n", lettermax);
                printf("\n");
                printf("Most unsuccesful student:\n");
                printf("Index: %d\n", index);
                printf("Score: %d\n", min);
                printf("Letter grade: %c\n", lettermin);
                printf("\n");
                printf("%2d student got letter grade 'A'\n", AA);
                printf("%2d student got letter grade 'B'\n", BB);
                printf("%2d student got letter grade 'C'\n", CC);
                printf("%2d student got letter grade 'D'\n", DD);
                printf("%2d student got letter grade 'F'\n", FF);
                printf("\n");
                printf("\nThe average Score of %d Student is %.2lf\n", (i-1), ort);
                printf("\n");
                break;
            default:
                if(selection != -1){
                    printf("\nFalse Selection!!!\n");
                }
        }
    }while(selection != -1);
}
