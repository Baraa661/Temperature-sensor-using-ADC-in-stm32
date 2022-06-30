# Temperature-detection-system-using-ADC-in-stm32
## A complete ADC driver for the ST.M32
## The Driver has the following services:
### 1- void ADC_Init(ADCConfigType* ConfigParamPtr) 
  Where ADCConfigType is a struct that c+ontains all the configuration parameters needed to initialize the STM ADC.
  The configuration parameters are listed below:
  1- Resolution (enum type)
  2- Conversion mode (single or continues) - (enum type).
  3- Reference voltage
  The following configuration macro shall be checked to enable or disable ADC Interrupt (USE_POLLING == 1)
### 2- void ADC_StartConv(unsigned char ChannelNum);
  The function is used to start a software conversion in the single conversion mode or start the first conversion in the continuous mode.
### 3- void ADC_GetConversionState(unsigned char* ConversionStatePtr);
  The function is enabled only when the configuration macro USE_POLLING is set to 1 and is used by the client to check if conversion is done (1) or not (0).
### 4- unsigned char ADC_ReadData(unsigned short int* DataPtr)
  The function used by the client to read the ADC value. The function returns 0 when there is a valid ADC value and the DataPtr is Dereferenced.. The function will   return 1 when there is no valid ADC value and the DataPtr is not dereferenced.
### 5- An ISR is implemented to notify that a conversion is completed. The implementation
  will be enabled only when the configuration macro USE_POLLING is set to 0.
### After implementing the ADC driver, it's used to interface an LM35 temperature sensor. The sensor temperature shall be continuously monitored and displayed on LM016 character LCD.
