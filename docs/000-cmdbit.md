
![logo](cmd25.png)

cmdbit.exe
----------

���������� �������� ����������� ������ � ������� [WIN](https://habr.com/ru/post/266831/) ��� [ELF](https://habr.com/ru/post/480642/)  
���������:

```
cmdbit.exe path/to/program.exe
```

- ������ `32`, ���� `program.exe` 32� ������.
- ������ `64`, ���� `program.exe` 64� ������.
- ������ `unknown`, �� ���� ��������� �������.

����� �������������:
--------------------

- ���� � �������� ������������ ����� ������� ������� ��������� ����,  
  �� ��������� �� � �� `32` � �� `64`, �� ��������� ����� `unknown`.  

- ���� ��������� �������, �� ������ ���� � ������������ �����, 
  ����� � stderr ����� ������: `invalid syntaxis.`  

- ���� ��������� �������, ������ �� ������������ ����, 
  ��������, ���� `no_exist`, ����� � stderr ����� ������: 
  `main(std::exception): can not open: 'no_exist'`  

- ���� ���� ����������, �� �� ����� �� �������� ��� �� ������� �������,
  (��������, �� ������� ����), ����� � stderr ����� ������: 
  `main(std::exception): ��������-�������������`  


