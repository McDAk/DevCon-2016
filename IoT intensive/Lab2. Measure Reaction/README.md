#DevCon 2016: IoT-�������� 

# ������������ 2: �������� ����� �������

� ���� ������ ��� ��������� ������� �����, ������� ����� �������� ����� ������� ������������ �� ��������� ����������.
��� ����� �� ��������� � ����������� ������, ��� �������� �� �����:

![LED Layout](../images/LEDLayout.PNG)

���������� �������� ��������� ����� ��������� �������� �������, ����� ���� �������� ����� (� ticks), ��������� �� ������� �� ������.

��� ��������� ������� ����� ������������ ������ `Stopwatch`. ��� ����� ������ � ������ ���������� ���������������� ���� �� ������ �� ����,
� ��� ���������� pullup (����� � ����������� ��������� ������ ���� ��������� � ������� ������):

```
var gpio = GpioController.GetDefault();
pin = gpio.OpenPin(26);        
pin.SetDriveMode(GpioPinDriveMode.InputPullUp);
```

����� ����� �������� �� ������ ����� ���������: �������� ������ � ������� `pin.Read()`, ��� ��������� ������� �� ����������
(�.�. ����� ��� ������� ������ ���������� ��������� �������):
```
var gpio = GpioController.GetDefault();
pin = gpio.OpenPin(26);        
pin.SetDriveMode(GpioPinDriveMode.InputPullUp);
pin.DebounceTimeout = TimeSpan.FromMilliseconds(50);
pin.ValueChanged += ButtonPressed;
...
private void ButtonPressed(GpioPin sender,
                           GpioPinValueChangedEventArgs args)
{
   if (args.Edge==GpioPinEdge.RisingEdge) { ... }
}
```
