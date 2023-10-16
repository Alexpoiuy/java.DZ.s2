1. Реализовать консольное приложение - телефонный справочник.
У одной фамилии может быть несколько номеров.
Пользователь может вводить команды:
1. ADD Ivanov 88005553535 - добавить в справочник новое значение. Первый аргумент - фамилия, второй - номер телефона
2. GET Ivanov - получить список всех номеров по фамилии
3. REMOVE Ivanov - удалить все номера по фамилии
4. LIST - Посмотреть все записи
5. EXIT - Завершить программу
Если при GET или REMOVE нужной фамилии нет, вывести информацию об этом

Пример взаимодействия (=> - это вывод на консоль):
ADD Ivanov 8 800 555 35 35
ADD Ivanov 8 800 100 10 10
GET Ivanov => [8 800 555 35 35, 8 800 100 10 10]
ADD Petrov 8 555 12 34
LIST => Ivanov = [8 800 5553535, 8 800 100 10 10], Petrov = [8 555 12 34]
REMOVE Ivanov
LIST => Petrov = [8 555 12 34]
GET NoName => Не найдена запись с фамилией "NoName"
REMOVE NoName => Не найдена запись с фамилией "NoName"

import java.util.*;

public class PhoneDirectory {
    private Map<String, List<String>> directory;

    public PhoneDirectory() {
        directory = new HashMap<>();
    }

    public void add(String lastName, String phoneNumber) {
        directory.computeIfAbsent(lastName, k -> new ArrayList<>()).add(phoneNumber);
    }

    public List<String> get(String lastName) {
        return directory.getOrDefault(lastName, new ArrayList<>());
    }

    public void remove(String lastName) {
        directory.remove(lastName);
    }

    public void list() {
        for (Map.Entry<String, List<String>> entry : directory.entrySet()) {
            System.out.println(entry.getKey() + " = " + entry.getValue());
        }
    }

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        PhoneDirectory phoneDirectory = new PhoneDirectory();

        while (true) {
            System.out.println("Введите команду (ADD, GET, REMOVE, LIST, EXIT):");
            String command = scanner.next();

            if (command.equals("ADD")) {
                String lastName = scanner.next();
                String phoneNumber = scanner.nextLine().trim();
                phoneDirectory.add(lastName, phoneNumber);
            } else if (command.equals("GET")) {
                String lastName = scanner.next();
                List<String> numbers = phoneDirectory.get(lastName);
                if (!numbers.isEmpty()) {
                    System.out.println(numbers);
                } else {
                    System.out.println("Не найдена запись с фамилией \"" + lastName + "\"");
                }
            } else if (command.equals("REMOVE")) {
                String lastName = scanner.next();
                phoneDirectory.remove(lastName);
            } else if (command.equals("LIST")) {
                phoneDirectory.list();
            } else if (command.equals("EXIT")) {
                break;
            } else {
                System.out.println("Неверная команда. Пожалуйста, попробуйте снова.");
            }
        }
    }
}

2. Реализовать консольное приложение - телефонный справочник.
У одной фамилии может быть несколько номеров.
Пользователь может вводить команды:
1. ADD Ivanov 88005553535 - добавить в справочник новое значение. Первый аргумент - фамилия, второй - номер телефона
2. GET Ivanov - получить список всех номеров по фамилии
3. REMOVE Ivanov - удалить все номера по фамилии
4. LIST - Посмотреть все записи
5. EXIT - Завершить программу
Если при GET или REMOVE нужной фамилии нет, вывести информацию об этом

Пример взаимодействия (=> - это вывод на консоль):
ADD Ivanov 8 800 555 35 35
ADD Ivanov 8 800 100 10 10
GET Ivanov => [8 800 555 35 35, 8 800 100 10 10]
ADD Petrov 8 555 12 34
LIST => Ivanov = [8 800 5553535, 8 800 100 10 10], Petrov = [8 555 12 34]
REMOVE Ivanov
LIST => Petrov = [8 555 12 34]
GET NoName => Не найдена запись с фамилией "NoName"
REMOVE NoName => Не найдена запись с фамилией "NoName"
Написать метод, который переведёт данное целое число в римский формат.

Алексей Дадашов, [17.10.2023 0:44]
import java.util.*;

public class PhoneDirectory {
    private Map<String, List<String>> directory;

    public PhoneDirectory() {
        directory = new HashMap<>();
    }

    public void add(String lastName, String phoneNumber) {
        directory.computeIfAbsent(lastName, k -> new ArrayList<>()).add(phoneNumber);
    }

    public List<String> get(String lastName) {
        return directory.getOrDefault(lastName, new ArrayList<>());
    }

    public void remove(String lastName) {
        directory.remove(lastName);
    }

    public void list() {
        for (Map.Entry<String, List<String>> entry : directory.entrySet()) {
            System.out.println(entry.getKey() + " = " + entry.getValue());
        }
    }

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        PhoneDirectory phoneDirectory = new PhoneDirectory();

        while (true) {
            System.out.println("Введите команду (ADD, GET, REMOVE, LIST, EXIT):");
            String command = scanner.next();

            if (command.equals("ADD")) {
                String lastName = scanner.next();
                String phoneNumber = scanner.nextLine().trim();
                phoneDirectory.add(lastName, phoneNumber);
            } else if (command.equals("GET")) {
                String lastName = scanner.next();
                List<String> numbers = phoneDirectory.get(lastName);
                if (!numbers.isEmpty()) {
                    System.out.println(numbers);
                } else {
                    System.out.println("Не найдена запись с фамилией \"" + lastName + "\"");
                }
            } else if (command.equals("REMOVE")) {
                String lastName = scanner.next();
                phoneDirectory.remove(lastName);
            } else if (command.equals("LIST")) {
                phoneDirectory.list();
            } else if (command.equals("EXIT")) {
                break;
            } else {
                System.out.println("Неверная команда. Пожалуйста, попробуйте снова.");
            }
        }
    }
}

Алексей Дадашов, [17.10.2023 0:54]
import java.util.*;

public class PhoneBook {
    private Map<String, List<String>> contacts;

    public PhoneBook() {
        contacts = new HashMap<>();
    }

    public void addContact(String name, String phoneNumber) {
        contacts.computeIfAbsent(name, k -> new ArrayList<>()).add(phoneNumber);
    }

    public void getContact(String name) {
        List<String> phoneNumbers = contacts.get(name);
        if (phoneNumbers != null) {
            System.out.println(phoneNumbers);
        } else {
            System.out.println("Не найдена запись с фамилией \"" + name + "\"");
        }
    }

    public void removeContact(String name) {
        List<String> removedNumbers = contacts.remove(name);
        if (removedNumbers != null) {
            System.out.println("Удалены все номера по фамилии \"" + name + "\"");
        } else {
            System.out.println("Не найдена запись с фамилией \"" + name + "\"");
        }
    }

    public void listAllContacts() {
        for (Map.Entry<String, List<String>> entry : contacts.entrySet()) {
            System.out.println(entry.getKey() + " = " + entry.getValue());
        }
    }

    public static void main(String[] args) {
        PhoneBook phoneBook = new PhoneBook();
        phoneBook.addContact("Ivanov", "88005553535");
        phoneBook.addContact("Ivanov", "88001001010");
        phoneBook.getContact("Ivanov");
        phoneBook.addContact("Petrov", "85551234");
        phoneBook.listAllContacts();
        phoneBook.removeContact("Ivanov");
        phoneBook.listAllContacts();
        phoneBook.getContact("NoName");
        phoneBook.removeContact("NoName");
    }
}
