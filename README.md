# arduino
Microsoft Visual Studio Solution File, Format Version 12.00
# Visual Studio 14
VisualStudioVersion = 14.0.23107.0
MinimumVisualStudioVersion = 10.0.40219.1
Project("{FAE04EC0-301F-11D3-BF4B-00C04F79EFBC}") = "MVCArduinoSQLEntityMant", "MVCArduinoSQLEntityMant\MVCArduinoSQLEntityMant.csproj", "{C3540383-2003-4C4A-877F-F2992BF8C276}"
EndProject
Global
	GlobalSection(SolutionConfigurationPlatforms) = preSolution
		Debug|Any CPU = Debug|Any CPU
		Release|Any CPU = Release|Any CPU
	EndGlobalSection
	GlobalSection(ProjectConfigurationPlatforms) = postSolution
		{C3540383-2003-4C4A-877F-F2992BF8C276}.Debug|Any CPU.ActiveCfg = Debug|Any CPU
		{C3540383-2003-4C4A-877F-F2992BF8C276}.Debug|Any CPU.Build.0 = Debug|Any CPU
		{C3540383-2003-4C4A-877F-F2992BF8C276}.Release|Any CPU.ActiveCfg = Release|Any CPU
		{C3540383-2003-4C4A-877F-F2992BF8C276}.Release|Any CPU.Build.0 = Release|Any CPU
	EndGlobalSection
	GlobalSection(SolutionProperties) = preSolution
		HideSolutionNode = FALSE
	EndGlobalSection
EndGlobal



/////// codigo del arduino

int pwr = 6;

//controlled leds
int blue = 12;
int green = 11;
int orange = 10;
int red = 9;

///set baudrate for serial connection
int baud = 9600;

///set delay time: 1 second
int time = 1000;

void setup() {
  //set pinmode and turn on power led
  pinMode(pwr, OUTPUT);
  digitalWrite(pwr, HIGH);
  
  //start serial
  Serial.begin(baud);

  //set pinmode for controlled leds
  pinMode(blue, OUTPUT);
  pinMode(green, OUTPUT);
  pinMode(orange, OUTPUT);
  pinMode(red, OUTPUT);
  // put your setup code here, to run once:
}
// the loop routine runs over
void loop()
//loop constantly scans for serial input
{
  //when connection is more than 1 begin if statements
  if (Serial.available() > 0)
  {
    //read serial input value
    int val = Serial.read();
    //begin if statement
    if (val == '1')
    {
      digitalWrite(blue, HIGH);
      delay(time);
      digitalWrite(blue, LOW);
    }
    if (val == '2')
    {
      digitalWrite(green, HIGH);
      delay(time);
      digitalWrite(green, LOW);
    }
    if (val == '3')
    {
      digitalWrite(orange, HIGH);
      delay(time);
      digitalWrite(orange, LOW);
    }
    if (val == '4')
    {
      digitalWrite(red, HIGH);
      delay(time);
      digitalWrite(red, LOW);
    }
    //flush the serial value
    Serial.flush();
  }
  // put your main code here, to run repeatedly:

}


/////////   base de dato sql server
create database LedArduino
use LedArduino

create table Led1
(
Pusaciones int not null Identity,
Texto varchar(50) not null
)

create table Led2
(
Pusaciones int not null Identity,
Texto varchar(50) not null
)

create table Led3
(
Pusaciones int not null Identity,
Texto varchar(50) not null
)

select * from Led1
select * from Led2
select * from Led3
