# Отчёт о тестировании Credit Card Number Validator

## Краткое описание

27.04.2020 - 27.04.2020 было проведено функциональное тестирование приложения Credit Card Number Validator.

На тестирование затрачено: 1 час

В результате тестирования выявлены следующие дефекты:
https://github.com/Alenovaalla/homework1.2java/issues/1

## Описание процесса тестирования

### В процессе тестирования использовались следующие артефакты:
* Отчет о тестировании

### В качестве тестовых данных использовались:
1. Написанный программистом код:

public class Main {
  public static void main(String[] args) {
    // TODO: подставлять номер карты нужно сюда между двойными кавычками, без пробелов
    String number = "5351719427810741";
    System.out.println(String.format("Result is %s", isValidCardNumber(number) ? "OK" : "FAIL"));
  }

  public static boolean isValidCardNumber(String number) {
    if (number == null) {
      return false;
    }

    if (number.length() != 16) {
      return false;
    }

    long result = 0;
    for (int i = 0; i < number.length(); i++) {
      int digit;
      try {
        digit = Integer.parseInt(number.charAt(i) + "");
      } catch (NumberFormatException e) {
        return false;
      }

      if (i % 2 == 0) {
        digit *= 2;
        if (digit > 9) {
          digit -= 9;
        }
      }
      result += digit;
    }

    return (result != 0) && (result % 10 == 0);
  }
}

2. Валидные номера карт 
* 4916995372355285 (Visa)
* 5160076700059855 (mastercard)
* 4532379783171275995 (Visa)
* 3534467994333253172 (JCB)
* 343196770405738 (American Express)
* 516007670005985 (American Express)
* 49169953723552850

### Тестирование производилось в следующем окружении:
* Windows 8.1 64X
* Java "11.0.7" 2020-04-14
