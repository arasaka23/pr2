import 'dart:io';
import 'dart:math';

void main() {
  final group = Group();
  
  while (true) {
    print('ЖУРНАЛ УСПЕВАЕМОСТИ ГРУППЫ');
    print('1. Вывести список студентов и предметов');
    print('2. Вывести все оценки студентов');
    print('3. Вывести средний балл по каждому предмету');
    print('4. Вывести средний балл каждого студента');
    print('5. Вывести лучшего студента');
    print('6. Вывести предмет с наименьшим средним баллом');
    print('7. Вывести общий средний балл группы');
    print('8. Вывести список всех предметов');
    print('9. Вывести студентов без двоек');
    print('10. Вывести студентов с оценками не ниже 4');
    print('0. Выход');
    
    stdout.write('Выберите действие: ');
    final choice = stdin.readLineSync() ?? '';
    
    switch (choice) {
      case '1':
        group.printStudentsAndSubjects();
        break;
      case '2':
        group.printAllGrades();
        break;
      case '3':
        group.printAverageBySubject();
        break;
      case '4':
        group.printAverageByStudent();
        break;
      case '5':
        group.printBestStudent();
        break;
      case '6':
        group.printWorstSubject();
        break;
      case '7':
        group.printOverallAverage();
        break;
      case '8':
        group.printAllSubjects();
        break;
      case '9':
        group.printStudentsWithoutTwos();
        break;
      case '10':
        group.printStudentsWithGradesNotLessThan4();
        break;
      case '0':
        print('Программа завершена.');
        return;
      default:
        print('Неверный выбор. Пожалуйста, выберите пункт от 0 до 10.');
    }
  }
}

class Student {
  final String name;
  final Map<String, int> grades;
  
  Student(this.name, this.grades);
}

class Group {
  final List<String> subjects = [
    'Математика',
    'Физика',
    'Программирование',
    'Английский язык',
    'История'
  ];
  
  late final List<Student> students;
  final Random random = Random();
  
  Group() {
    _initializeStudents();
  }
  
  void _initializeStudents() {
    final names = [
      'Иванов Иван',
      'Петров Петр',
      'Сидорова Анна',
      'Козлова Мария',
      'Смирнов Алексей',
      'Васильева Елена',
      'Кузнецов Дмитрий',
      'Морозова Ольга'
    ];
    
    students = names.map((name) {
      final grades = <String, int>{};
      for (var subject in subjects) {
        grades[subject] = random.nextInt(4) + 2;
      }
      return Student(name, grades);
    }).toList();
  
    students[0].grades['Математика'] = 5;
    students[0].grades['Программирование'] = 5;
    students[1].grades['Физика'] = 2;
    students[2].grades['Программирование'] = 5;
    students[3].grades['Математика'] = 2;
    students[4].grades['История'] = 5;
    students[5].grades['Английский язык'] = 5;
  }
  
  void printStudentsAndSubjects() {
    print('\n СПИСОК СТУДЕНТОВ');
    for (int i = 0; i < students.length; i++) {
      print('${i + 1}. ${students[i].name}');
    }
    
    print('\nСПИСОК ПРЕДМЕТОВ ');
    for (int i = 0; i < subjects.length; i++) {
      print('${i + 1}. ${subjects[i]}');
    }
  }
  
  void printAllGrades() {
    print('\nОЦЕНКИ СТУДЕНТОВ');
    for (var student in students) {
      print('\n${student.name}:');
      for (var subject in subjects) {
        print('  $subject: ${student.grades[subject]}');
      }
    }
  }
  
  void printAverageBySubject() {
    print('\nСРЕДНИЙ БАЛЛ ПО ПРЕДМЕТАМ');
    for (var subject in subjects) {
      double sum = 0;
      for (var student in students) {
        sum += student.grades[subject]!;
      }
      double average = sum / students.length;
      print('$subject: ${average.toStringAsFixed(2)}');
    }
  }
  
  void printAverageByStudent() {
    print('\nСРЕДНИЙ БАЛЛ ПО СТУДЕНТАМ ');
    for (var student in students) {
      double sum = 0;
      for (var subject in subjects) {
        sum += student.grades[subject]!;
      }
      double average = sum / subjects.length;
      print('${student.name}: ${average.toStringAsFixed(2)}');
    }
  }
  
  void printBestStudent() {
    print('\nЛУЧШИЙ СТУДЕНТ');
    String bestStudent = '';
    double bestAverage = 0;
    
    for (var student in students) {
      double sum = 0;
      for (var subject in subjects) {
        sum += student.grades[subject]!;
      }
      double average = sum / subjects.length;
      
      if (average > bestAverage) {
        bestAverage = average;
        bestStudent = student.name;
      }
    }
    
    print('$bestStudent (средний балл: ${bestAverage.toStringAsFixed(2)})');
  }
  
  void printWorstSubject() {
    print('\n ПРЕДМЕТ С НАИМЕНЬШИМ СРЕДНИМ БАЛЛОМ');
    String worstSubject = '';
    double lowestAverage = 6;
    
    for (var subject in subjects) {
      double sum = 0;
      for (var student in students) {
        sum += student.grades[subject]!;
      }
      double average = sum / students.length;
      
      if (average < lowestAverage) {
        lowestAverage = average;
        worstSubject = subject;
      }
    }
    
    print('$worstSubject (средний балл: ${lowestAverage.toStringAsFixed(2)})');
  }
  
  void printOverallAverage() {
    print('\nОБЩИЙ СРЕДНИЙ БАЛЛ ГРУППЫ');
    double totalSum = 0;
    int totalGrades = 0;
    
    for (var student in students) {
      for (var subject in subjects) {
        totalSum += student.grades[subject]!;
        totalGrades++;
      }
    }
    
    double average = totalSum / totalGrades;
    print('${average.toStringAsFixed(2)}');
  }
  
  void printAllSubjects() {
    print('\n ВСЕ ПРЕДМЕТЫ ');
    for (int i = 0; i < subjects.length; i++) {
      print('${i + 1}. ${subjects[i]}');
    }
    print('Всего предметов: ${subjects.length}');
  }
  
  void printStudentsWithoutTwos() {
    print('\n СТУДЕНТЫ БЕЗ ДВОЕК ');
    bool found = false;
    
    for (var student in students) {
      bool hasTwo = false;
      for (var subject in subjects) {
        if (student.grades[subject] == 2) {
          hasTwo = true;
          break;
        }
      }
      
      if (!hasTwo) {
        print(student.name);
        found = true;
      }
    }
    
    if (!found) {
      print('Нет студентов без двоек');
    }
  }
  
  void printStudentsWithGradesNotLessThan4() {
    print('\n СТУДЕНТЫ С ОЦЕНКАМИ НЕ НИЖЕ 4 ');
    bool found = false;
    
    for (var student in students) {
      bool allGood = true;
      for (var subject in subjects) {
        if (student.grades[subject]! < 4) {
          allGood = false;
          break;
        }
      }
      
      if (allGood) {
        print(student.name);
        found = true;
      }
    }
    
    if (!found) {
      print('Нет студентов с оценками не ниже 4');
    }
  }
}
