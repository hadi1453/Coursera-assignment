

```R
pml.train <- read.csv("pml-training.csv")
```


```R
pml.test <- read.csv("pml-testing.csv")
```


```R
table(pml.train$classe)
```


    
       A    B    C    D    E 
    5580 3797 3422 3216 3607 



```R
dim(pml.train)
```


<ol class=list-inline>
	<li>19622</li>
	<li>160</li>
</ol>




```R
dim(pml.test)
```


<ol class=list-inline>
	<li>20</li>
	<li>160</li>
</ol>




```R
library(MASS)
library(lattice)
library(ggplot2)
library(caret)
```


```R
library(rpart)
```


```R
model <- train(classe~., data = pml.train, method = 'rpart')
```


```R
model1
```

CART 

19622 samples
  159 predictor
    5 classes: 'A', 'B', 'C', 'D', 'E' 

No pre-processing
Resampling: Bootstrapped (25 reps) 
Summary of sample sizes: 406, 406, 406, 406, 406, 406, ... 
Resampling results across tuning parameters:

  cp         Accuracy   Kappa    
  0.2323232  0.7915072  0.7379420
  0.2356902  0.7513342  0.6874440
  0.2659933  0.4765105  0.3347537

Accuracy was used to select the optimal model using  the largest value.
The final value used for the model was cp = 0.2323232. 

This model can recognise the human activity, and classify them into 5 class og A, B, C, D and E.


```R
prediction <- predict(model, pml.test)
```

We can predict the test cases based on the machine learning model.
