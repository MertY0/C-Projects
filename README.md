#include<stdio.h>
#include<stdlib.h>

float odevhesapla(int odevsayisi, long long int ogrencino){
	int i;
    float ortalama,toplam=0;
	float odevkumesi[20];

	for(i=0;i<odevsayisi;i++){
		printf("Enter %d.Homework Score : ",i+1);
		scanf("%f", & odevkumesi[i]);
	}


	for (i = 0; i < odevsayisi; i++) {
		toplam += odevkumesi[i];

	}
	
	ortalama = toplam / odevsayisi;

	return ortalama;
}




float hesapla(int odevsayisi,long long int ogrencino) {
	float vize, final, ortalama;
	printf("Enter the midterm score for student number %lld : ",ogrencino);	
	scanf("%f", &vize);
	printf("Enter the final score for student number %lld : ",ogrencino);
	scanf("%f", &final);

	if (odevsayisi == 0) {
		ortalama = vize * 0.6 + final * 0.4;
	}
	else {
		float odev = odevhesapla(odevsayisi, ogrencino);
		ortalama = vize * 0.35 + final * 0.4 + odev * 0.25;

	}



		return ortalama;
}

int main() {
	int odevsayisi,x,sayac=0,i;
	float toplam = 0;
	float dusuk=100,yuksek=0;
	long long int ogrencino;
	float ogrencinotlari[20];
	printf("Exam Grade Calculator\n\n");
	printf("Enter the number of homeworks\n");
	scanf("%d", &odevsayisi);

	while (1){
		printf("\n\nEnter the student number : ");
	    scanf("%lld", & ogrencino);
		float sonuc = hesapla(odevsayisi, ogrencino);
		printf("The average grade of Student Number %lld : %.3f\n", ogrencino,sonuc);
		toplam += sonuc;
		ogrencinotlari[sayac] = sonuc;
		sayac++;
		printf("Do you want to add a new student? (0 or 1)");
		scanf("%d", &x);
		if (x == 0) {
			break;
		}
		}


	for (i = 0; i < sayac;i++) {
		if(ogrencinotlari[i]<dusuk){
		dusuk = ogrencinotlari[i];}

		if (ogrencinotlari[i] > yuksek) {
			yuksek = ogrencinotlari[i];
		}


	}



	printf("The class grade average : %.3f\n", toplam / sayac);
	printf("The class's lowest grade : %.3f\n",dusuk);
	printf("The class's highest grade : %.3f\n",yuksek);
	return 0;
}
