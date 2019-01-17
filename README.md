# 2019-Zoukeepers

## States
Read - Read states are for reading sensor inputs or user control inputs from the joystick.
Calc - Calc states are for calculating the correct outputs for the actuators of the robot, but does not execute the output.
Write - Executes the outputs from Calc state to the actuators.

## Controls

Joysticks used are Logitec 3D Pros

### Joystick Right - Drive

| Input           | Function             |
| --------------- | -------------------- |
| Y Axis Forward  | Drive forward        |
| Y Axis Backward | Drive backward       |
| Z Axis Left     | Turn left            |
| Z Axis Right    | Turn right           |
| Trigger         | Ball intake in       |
| Thumb           | Ball intake out      |
| Bottom 11       | Toggle jump solenoid |

### Joystick Left - Actuators

| Input           | Function                         |
| --------------- | -------------------------------- |
| Y Axis Forward  | Lift down                        |
| Y Axis Backward | Lift up                          |
| Trigger         | Toggle wrist                     |
| Thumb Button    | Lift to bottom (for ball pickup) |
| Top 3           | Trigger hatch deploy             |
| Base 7          | Lift to top ball goal            |
| Base 9          | Lift to middle ball goal         |
| Base 11         | Lift to bottom ball goal         |
| Base 8          | Lift to top hatch goal           |
| Base 10         | Lift to middle hatch goal        |
| Base 12         | Lift to bottom hatch goal        |

## TypeDefs

### typedef_enum_Begin_State

Begin state machine

| Name               | Number |
| ------------------ | ------ |
| Network_Setup      | 0      |
| Joy_Stick_Setup    | 1      |
| Drive_Train_Setup  | 2      |
| Ball_Intake_Setup  | 3      |
| Wrist_Setup        | 4      |
| Hatch_Deploy_Setup | 5      |
| Compressor_Setup   | 6      |
| Lift_Setup         | 7      |
| Gyro_Setup         | 8      |
| Stop               | 9      |

### typedef_enum_Teleop_State

Teleop state machine

| Name                | Number |
| ------------------- | ------ |
| Read NT             | 0      |
| Read Joy            | 1      |
| Read Gyro           | 2      |
| Read Drive Encoders | 3      |
| Read Limit          | 4      |
| Calc Vision         | 5      |
| Calc Wrist          | 6      |
| Calc Drive          | 7      |
| Calc Fly            | 8      |
| Calc Lift           | 9      |
| Calc Hatch          | 10     |
| Write Wrist         | 11     |
| Write Drive         | 12     |
| Write Fly           | 13     |
| Write Lift          | 14     |
| Write Hatch         | 15     |
| Write Jump          | 16     |
| Write NT            | 17     |

### typedef_cluster_Teleop_Local_Data

| Name             | Type                     | I/O    |
| ---------------- | ------------------------ | ------ |
| JoyStick_L       | typedef_cluster_Joystick | Input  |
| JoyStick_R       | typedef_cluster_Joystick | Input  |
| Lift_Lower_Limit | Boolean                  | Input  |
| Lift_Upper_Limit | Boolean                  | Input  |
| Switch_Intake    | Boolean                  | Input  |
| Encoder_Lift     | Double                   | Input  |
| Drive_Enc_Left   | Double                   | Input  |
| Drive_Env_Right  | Double                   | Input  |
| Gyro_Angle       | Double                   | Input  |
| Drive_Forward    | Double                   | Output |
| Drive_Twist      | Double                   | Output |
| Motor_Intake     | Double                   | Output |
| Motor_Lift       | Double                   | Output |
| Sol_Wrist        | Boolean                  | Output |
| Sol_Hatch        | Boolean                  | Output |
| Sol_Jump         | Boolean                  | Output |

### typedef_cluster_Joystick

| Name      | Type    |
| --------- | ------- |
| X         | Double  |
| Y         | Double  |
| Z         | Double  |
| Throttle  | Double  |
| Trigger   | Boolean |
| Thumb     | Boolean |
| Top 3     | Boolean |
| Top 4     | Boolean |
| Top 5     | Boolean |
| Top 6     | Boolean |
| Bottom 7  | Boolean |
| Bottom 8  | Boolean |
| Bottom 9  | Boolean |
| Bottom 10 | Boolean |
| Bottom 11 | Boolean |
| Bottom 12 | Boolean |

### typedef_enum_refnums

| Name             | Number |
| ---------------- | ------ |
| Joy_L            | 0      |
| Joy_R            | 1      |
| Drive_Motors     | 2      |
| Intake_Motor     | 3      |
| Wrist_Solenoid   | 4      |
| Hatch_Solenoid   | 5      |
| Compressor       | 6      |
| Lift_Motor       | 7      |
| Lift_Motor_2     | 8      |
| Gyro             | 9      |
| Drive_Enc_L      | 10     |
| Drive_Enc_R      | 11     |
| Lift_Lower_Limit | 12     |
| Lift_Upper_Limit | 13     |
| Ball_Switch      | 14     |
| Jump_Solenoid    | 15     |

## Networking

| Name      | Range         |
| --------- | ------------- |
| IP Range  | 10.37.92.0/24 |
| Router    | 10.37.92.1    |
| Rio       | 10.37.92.30   |
| LimeLight | 10.37.92.11   |

## Hardware

| Name                         | Port  |
| ---------------------------- | ----- |
| RightDrive encoder A channel | DIO 0 |
| RightDrive encoder B channel | DIO 1 |
| LeftDrive encoder A channel  | DIO 2 |
| LeftDrive encoder B channel  | DIO 3 |
| Ball Intake Switch           | DIO 4 |
| Sparkx Left 1                | PWM 0 |
| Sparkx Left 2                | PWM 1 |
| Sparkx Right 1               | PWM 2 |
| Sparkx Right 2               | PWM 3 |
| Sparx Intake                 | PWM 4 |
| PCM ID                       | 0     |
| Pneumatics Wrist             | 0 & 1 |
| Pneumatics Hatch Pistons     | 2 & 3 |
| Pneumatics Jump Piston       | 4 & 5 |

### PID Tuning

| Name   | Value |
| ------ | ----- |
| P      | 3     |
| I      | 0.0001|
| D      | 0     |

### Related Issue - Phoneix Libraries cleared on RoboRIO reboot
https://github.com/CrossTheRoadElec/Phoenix-Releases/issues/1
