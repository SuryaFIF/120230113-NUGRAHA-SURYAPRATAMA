# 120230113-NUGRAHA-SURYAPRATAMA
Laporan Praktikum Week 4

Program Bahasa C
#include <stdio.h>
#include <stdlib.h>
#include <string.h>

#define MAX_LENGTH 2024
#define MIN_LENGTH 1945

void lessThanRequired(int *lengthOfText) {
    printf("The length of your text is less than specified, please update your text\n");
    *lengthOfText = MIN_LENGTH;
}

void equalThanRequired() {
    printf("Thank you, Your text length is correct\n");
}

void moreThanRequired(int *lengthOfText) {
    printf("Your text is too long, please reduce the text\n");
    *lengthOfText = MIN_LENGTH;
}

int checkLengthRequirement(char* text) {
    int length = strlen(text);
    if (length < MIN_LENGTH)
        return 0;
    else if (length == MIN_LENGTH)
        return 1;
    else
        return 2;
}

int main() {
    int lengthOfText, selectOption;
    FILE *fptr = NULL;
    char text[MAX_LENGTH];

    fptr = fopen("file.txt", "r");

    if (fptr == NULL) {
        printf("Error");
        exit(1);
    }

    fgets(text, MAX_LENGTH, fptr);

    fclose(fptr);

    selectOption = checkLengthRequirement(text);
     // TODO
    // Pada fungsi checkLenghtRequirement akan mengembalikan sebuah angka
    // angka tersebut digunakan untuk memilih secara otomatis salah satu fungsi yang harus diisi
    // jika fungsi checkLenghtRequirement() mengembalikan nilai 0, maka
    //      tampilkan - > The length of your text is less than specified, please update your text
    //      update nilai lengthOfText ke minimum requirement melalui pointer menggunakan operasi aritmatika

    // jika fungsi checkLenghtRequirement() mengembalikan nilai 1, maka
    //      tampilkan - > Thank you, Your text length is correct

    // jika fungsi checkLenghtRequirement() mengembalikan nilai 2, maka
    //      tampilkan - > Your text is to long, please reduce the text
    //      update nilai lengthOfText ke minimum requirement melalui pointer menggunakan operasi aritmatika
    //
    // Catatan :
    //      - tidak diperkenankan menggunakan if atau switch dalam perpindahan fungsi
    //        sesuai dengan requirement diatas.
    //      - baris kode tidak lebih dari 100 (include comment ini)
    //      - tidak diperkenankan mengganti yang tertera pada starter code dalam alasan apapun


    // Function pointers to avoid using if or switch
    void (*options[3])(int *) = {lessThanRequired, equalThanRequired, moreThanRequired};
    options[selectOption](&lengthOfText);

    printf("\nThe Length is updated to %d", lengthOfText);

    return 0;
}

Penjelasan Source Code

Pendefinisian Konstanta dan Prototipe Fungsi:

MAX_LENGTH dan MIN_LENGTH didefinisikan sebagai konstanta yang menentukan panjang maksimum dan minimum teks.
Prototipe fungsi lessThanRequired, equalThanRequired, dan moreThanRequired dideklarasikan untuk memberikan pesan sesuai dengan panjang teks yang diinput.
Fungsi lessThanRequired:

Fungsi ini mengambil alamat dari panjang teks dan menampilkan pesan jika panjang teks kurang dari panjang minimum yang ditentukan.
Panjang teks diupdate ke nilai minimum menggunakan pointer.
Fungsi equalThanRequired:

Fungsi ini hanya menampilkan pesan jika panjang teks sama dengan panjang minimum yang ditentukan.
Fungsi moreThanRequired:

Fungsi ini mengambil alamat dari panjang teks dan menampilkan pesan jika panjang teks lebih dari panjang minimum yang ditentukan.
Panjang teks diupdate ke nilai minimum menggunakan pointer.
Fungsi checkLengthRequirement:

Fungsi ini menerima teks dan mengembalikan nilai berdasarkan panjang teks relatif terhadap panjang minimum yang ditentukan.
Jika panjang teks kurang dari panjang minimum, fungsi mengembalikan 0.
Jika panjang teks sama dengan panjang minimum, fungsi mengembalikan 1.
Jika panjang teks lebih dari panjang minimum, fungsi mengembalikan 2.
Fungsi main:

Dalam fungsi main, file "file.txt" dibuka dan teksnya dibaca menggunakan fgets.
Nilai yang dikembalikan oleh checkLengthRequirement disimpan dalam variabel selectOption.
Array options dari fungsi pointer dibuat, yang merujuk ke fungsi lessThanRequired, equalThanRequired, dan moreThanRequired.
Fungsi pointer dipanggil berdasarkan nilai selectOption untuk menampilkan pesan dan memperbarui nilai panjang teks jika diperlukan.
Terakhir, panjang teks yang diperbarui dicetak ke layar.
