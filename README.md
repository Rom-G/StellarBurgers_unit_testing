# Stellar Burgers — юнит-тестирование

Юнит-тесты сервиса заказа бургеров.
Покрывается класс `Burger` с использованием моков, стабов, верификации вызовов и параметризации.

## Технологии

![Java](https://img.shields.io/badge/Java-11-orange)
![Maven](https://img.shields.io/badge/Maven-3.8-blue)
![JUnit](https://img.shields.io/badge/JUnit-4.13.2-red)
![Mockito](https://img.shields.io/badge/Mockito-3.x-green)
![JaCoCo](https://img.shields.io/badge/coverage-100%25-brightgreen)

## Структура проекта

    src
    ├── main
    │   └── java/ru/stellarburgers        — код программы: Bun, Burger, Ingredient, IngredientType, Database
    └── test
        └── java/ru/stellarburgers
            ├── dto                       — тестовые данные: BunData, IngredientData
            ├── BurgerParameterizedTest   — цена и чек: 5 параметризованных наборов
            ├── BurgerChangeIngredientsTest — removeIngredient, moveIngredient
            ├── BurgerCallMultiplicityTest  — verify: количество вызовов зависимостей
            └── ReceiptData               — эталонные чеки для сравнения

Отчёты о прогоне: `docs/jacoco` (покрытие) и `docs/surefire` (статус тестов).

## Как запустить

1. Клонировать репозиторий:

        git clone https://github.com/Rom-G/StellarBurgers_unit_testing.git

2. Запустить тесты:

        mvn clean test

3. Собрать отчёты:

        mvn verify

4. Посмотреть результаты:
    - **JaCoCo** (покрытие): `docs/jacoco/index.html` — актуальный отчёт лежит в репозитории;
    - **Surefire** (статус тестов): `docs/surefire/index.html`.

## Что покрыто

Сценарии, обоснование техник и граничные случаи — в [TEST_PLAN.md](TEST_PLAN.md).

| Тестовый класс | Методы Burger | Приёмы |
|---|---|---|
| BurgerParameterizedTest | getPrice, getReceipt | параметризация, моки, стабы |
| BurgerChangeIngredientsTest | removeIngredient, moveIngredient | моки, Assume для граничного случая |
| BurgerCallMultiplicityTest | getPrice, getReceipt | verify, spy |

## Покрытие

**100%** по классу Burger (JaCoCo): 133/133 instructions, 4/4 branches, 7/7 methods, 23/23 lines.

![Отчёт JaCoCo](docs/jacoco-report.png)
