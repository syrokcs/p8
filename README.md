#include <stdio.h>
#include <string.h>
#include <stdlib.h>

// Функція для обчислення факторіалу
int factorial(int n) {
    int result = 1;
    for (int i = 1; i <= n; i++) {
        result *= i;
    }
    return result;
}

// Функція для обчислення кількості анаграм
int countAnagrams(char* word) {
    int length = strlen(word);

    // Обчислюємо загальну кількість анаграм
    int totalAnagrams = factorial(length);

    // Обчислюємо факторіали кількості повторюваних букв
    int letterCount[26] = {0};  // Масив для зберігання кількості кожної букви
    for (int i = 0; i < length; i++) {
        letterCount[word[i] - 'A']++;
    }
    for (int i = 0; i < 26; i++) {
        if (letterCount[i] > 1) {
            totalAnagrams /= factorial(letterCount[i]);
        }
    }

    return totalAnagrams;
}

int main() {
    char word[15];

    // Зчитуємо слово від користувача
    printf("Введіть слово: ");
    scanf("%s", word);

    // Рахуємо кількість анаграм
    int anagramCount = countAnagrams(word);

    // Виводимо результат
    printf("Кількість можливих анаграм: %d\n", anagramCount);

    return 0;
}
