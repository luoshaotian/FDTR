# FDTR_fit.exe
The program used 1D or 2D thermal model to fit different parameter we needed. You only need prepare csv file containning frequency & phase information of probe and pump( post sample) and a par file storing the original information of each layer.
The software interface is shown below.

![](https://github.com/luoshaotian/FDTR_fit/tree/main/pic/6.png)

In the software interface, 'Drop Down' button can switch the selection symbolized three methods mentioned above. When you select 'analysis' button, pre-analysis function is selected. 

In the configure panel, outliers can set to 0 or 1, 1 means software will automatically delete the outliers from the signal data. 

frequency point is recommended to set larger than your signal data number.(default is 50). 

Pump/probe radius need a real value from your FDTR system. 

low/high freq is the range of  modulation frequency. 

'Change degree' allow you to change the final phase of signal (we hope we can get better result by changing degree). 

'DimensionSelect': when penatration depth is larger than light spot radius we select '2' dimension model, else, we select '1' diemension model.

'DataToDelete': delete some bad data. e.g.  '1-10'  means that you want to delete the first ten data(you can not delete the tail data , it will cause error)


## Data preparation
When use this software to fit FDTR model, you must prepare three kinds of file for it.

i.e.

- .par file
- sample signal file
- reference signal file

In the software interface, use 'selectParfile' button the choose par file , 'SelectRfile' to choose reference  signal file, 'SelectSfile' to choose sample signal file. It should be noted that par file name should be named by the model.  For the materials 80nmAu-500nm$SiO_2$-30nm$Al_2O_3$-Si, the par file name is **Au_80_SiO2_500_Al2O3_30_Si_1.par**, The '1' means that Si  can be considered infinitely thick and it is necessary.  


All of these have an example in this repo. In the par file, the heat model was noted. And you need get two kinds of signal from your FDTR system. Detail messages
can find from [here](https://github.com/luoshaotian/FDTR_fit/tree/main/Example/README.md)     

## Function introduction

There have three functions in this software which are FDTR fitting, sensitivity analysis, and pre-analysis. 

### pre-analysis

When you decide to use FDTR to measure material's thermal conductivity, the first thing you should do is making a par file for the model. For example, there is a 
sample model which was made by 80nmAu-500nm$SiO_2$-30nm$Al_2O_3$-Si. And I will make a par file for it as the picture shown below.

![](https://github.com/luoshaotian/FDTR_fit/tree/main/pic/5.png)

Actually, this step is "Data preparation". However, when I make samples, whether it have some methods to guide me so that my samples can measure good data?
The pre-analysis do this thing.

**Steps:**
1. Select 'analysis' selection in 'Drop Down' button.
2. Clean the number in 'FitPars' button ( let it empty)
3. Use 'SelectParFile' button to select your par file
4. Use 'SelectSFile' button to select your sample singal file
5. Use 'SelectRarFile' button to select your reference signal file
6. Click 'Run' button
7. Change a parameter's value in your par file
8. Repeate step 6 and 7

These steps will create some curves in the left  figure. If you slightly change one parameter while those curves have a big difference, it means the original parameter have a good sensitivity of phase.( Using this value of that parameter can finally get a decent result). When you want to make a sample and wish it can get a good fitting result, you can use above steps by changing sample thickness to ensure what thickness can get better fitting result.

### sensitivity

sensitivity analysis is an important analysis in FDTR, it answer the question: Whether some parameters can be fitted simultaneously. You should know what is sensitivity analysis firstly.

**Steps**
1. Select 'sensitivity' selection in 'Drop Down' button.
2. Use 'SelectParFile' button to select your par file
3. Use 'SelectSFile' button to select your sample singal file
4. Use 'SelectRarFile' button to select your reference signal file
5. write a parameter position in 'FitPars' box.    e.g.  32 means the parameter in  the third row and second column  in the par file.


### final_result

It can fit some parameter you wrote in 'FitPars' box. And the fitting result will show in log panel.

**Steps**
1. Select 'final_result' selection in 'Drop Down' button.
2. Use 'SelectParFile' button to select your par file
3. Use 'SelectSFile' button to select your sample singal file
4. Use 'SelectRarFile' button to select your reference signal file
5. write some parameters position in 'FitPars' box.    e.g.  3231 means the parameters in  the third row and second column  and in  the third row and first column  in the par file.

And you will find the two parameter's fitting value is shown in log panel. If you want to see the orignal data you can  Select 'pump'/'probe'/'pump-probe' selection in 'Drop Down' button. Before changing the selection, you'd better to use 'CleanSreen' button to clean the figure. Only when you select 'sensitivity' in 'Drop Down', the right figure can be clean.



