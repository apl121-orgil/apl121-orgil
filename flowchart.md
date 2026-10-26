# APL121 orgil

Алгоритм ба программчлалын хэл хичээлийн даалгаврууд.

## Программууд
- hello.c - анхны С программ (1-р долоо хоног)

## Хөрвүүлэх
`gcc hello.c -o hello` гэж хөрвүүлээд `./hello` гэж ажиллуулна.ss
#include <stdio.h>

float calculateTariff(float km, float min, int hour) {
    float price = 5000.0; 
    float total = 0.0;

    if (km > 2) {
        price = price + (km - 2) * 1500;
    }
    
    price = price + (min * 200); 

    if (hour >= 22 || hour < 6) {
        total = price + (price * 0.2);
    } else {
        total = price;
    }

    return total;
}

int main() {
    float km, min, totalPrice;
    int hour;

    do {
        printf("Явсан зай (км)-ээ оруулна уу: ");
        scanf("%f", &km);
        printf("Хүлээлгийн минут оруулна уу: ");
        scanf("%f", &min);
        printf("Яваа цагаа оруулна уу (0-23): ");
        scanf("%d", &hour);

        if (km < 0 || min < 0 || hour < 0 || hour > 23) {
            printf("[Алдаа] Буруу утга орууллаа. Дахин оролдоно уу!\n");
        }
    } while (km < 0 || min < 0 || hour < 0 || hour > 23);

    totalPrice = calculateTariff(km, min, hour);
    printf("--> Нийт төлөх дүн: %.2f төгрөг\n\n", totalPrice);

    printf("--- 1-10 км хүртэлх тарифын хүснэгт ---\n");
    printf("%-10s | %-15s\n", "Зай (км)", "Төлөх дүн");
    printf("----------------------------------\n");
    for (int i = 1; i <= 10; i++) {
        float tPrice = calculateTariff(i, 0, 12);
        printf("%-10d | %-15.2f\n", i, tPrice);
    }
    printf("\n");

    float trip1 = calculateTariff(3, 0, 10);  
    float trip2 = calculateTariff(7, 5, 23);  
    float trip3 = calculateTariff(1, 10, 14); 

    printf("--- 3 аяллын жишиг ба эрэмбэлэлт ---\n");
    printf("Аялал 1 (3км): %.2f₮\n", trip1);
    printf("Аялал 2 (7км, шөнө): %.2f₮\n", trip2);
    printf("Аялал 3 (1км, хүлээлттэй): %.2f₮\n", trip3);

    if (trip1 <= trip2 && trip1 <= trip3) {
        printf("Хамгийн хямд аялал: Аялал 1 (%.2f₮)\n", trip1);
    } else if (trip2 <= trip1 && trip2 <= trip3) {
        printf("Хамгийн хямд аялал: Аялал 2 (%.2f₮)\n", trip2);
    } else {
        printf("Хамгийн хямд аялал: Аялал 3 (%.2f₮)\n", trip3);
    }

    return 0;


    Эхлэл
  Хувьсагчид зарлах: km, min, price, total (Real), hour, i (Integer)
  Давталт (Do-While)
     Оролт авах: km, min, hour
     Хэрэв (km < 0 OR min < 0 OR hour < 0 OR hour > 23) бол буруу утга гэж үзэх
  Цикл төгсгөл (Зөв утга орох хүртэл дахин давтана)

  total = CalculateTariff(km, min, hour)
  Гаралт: total

  Цикл (i = 1-ээс 10 хүртэл)
     Гаралт: i болон CalculateTariff(i, 0, 12)

  trip1 = CalculateTariff(3, 0, 10)
  trip2 = CalculateTariff(7, 5, 23)
  trip3 = CalculateTariff(1, 10, 14)
  If (trip1 <= trip2 AND trip1 <= trip3) бол trip1 хямд
  Else if (trip2 <= trip1 AND trip2 <= trip3) бол trip2 хямд
  Else trip3 хямд
Төгсгөл

| № | Тестийн төрөл | Оролт (km, min, hour) | Flowgorithm гаралт | C кодын гаралт | Төлөв |
|---|---|---|---|---|---|
| 1 | Энгийн утга | 3 км, 0 мин, 14 цаг | 6500.0₮ | 6500.00₮ | Зөв |
| 2 | **Хилийн утга** (Яг 2 км) | 2 км, 0 мин, 12 цаг | 5000.0₮ | 5000.00₮ | Зөв |
| 3 | Шөнийн нэмэгдэлтэй | 5 км, 2 мин, 23 цаг | 11400.0₮ | 11400.00₮ | Зөв |
| 4 | Хүлээлгийн минуттай | 1 км, 10 мин, 15 цаг | 7000.0₮ | 7000.00₮ | Зөв |
| 5 | **Буруу оролт** | -2 км, 5 мин, 10 цаг | Дахин асуух | Дахин асуух | Зөв |  

# Сэдэв №11 - Таксины тарифын тооцоолуур

## Дүрмүүд ба хязгаарлалт:
- Суурь үнэ: 5000₮ (Эхний 2 км багтана)
- Нэмэлт км бүрт: 1500₮
- Хүлээлгийн минут тутамд: 200₮
- Шөнийн нэмэгдэл: 22:00 - 06:00 цагийн хооронд нийт үнийн дүн дээр 20% нэмэгдэнэ.

## Программ ажиллуулах команд (GCC):
```bash
gcc main.c -o main
./main 



}

