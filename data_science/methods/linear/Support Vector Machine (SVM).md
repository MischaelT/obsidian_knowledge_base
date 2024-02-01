🏷️: #linear_algebra #svm #linear_model

🔗:  https://www.analyticsvidhya.com/blog/2021/10/support-vector-machinessvm-a-complete-guide-for-beginners
### Coursera
- A Support Vector Machine is a supervised algorithm that can classify cases by finding a separator.
- ![[Pasted image 20230522163557 1.png]]
- We just looking for equation of plane that separates the data
- ![[Pasted image 20230522164041 1.png]]
#math #linear_algebra 
- ![[Pasted image 20230522164451 1.png]]
- ![[Pasted image 20230522164535 1.png]]
- ![[Pasted image 20230522164639 1.png]]
### Support vector machine MIT lecture
https://www.youtube.com/watch?v=_PwhiWxHK8o&ab_channel=MITOpenCourseWare


![[Pasted image 20230822172819.png]]
- The primary goal is to find w and to make this rule true

![[Pasted image 20230822173442.png]]

### Article
🔗:  https://www.analyticsvidhya.com/blog/2021/10/support-vector-machinessvm-a-complete-guide-for-beginners

- Depending on the number of features you have you can either choose Logistic Regression or SVM.
  SVM works best when the dataset is small and complex. It is usually advisable to first use logistic regression and see how does it performs, if it fails to give a good accuracy you can go for SVM without any kernel.
#### Linear SVM
-  **Support Vectors:** These are the points that are closest to the hyperplane. A separating line will be defined with the help of these data points.
- **Margin:** it is the distance between the hyperplane and the observations closest to the hyperplane (support vectors). In SVM large margin is considered a good margin. There are two types of margins **hard margin** and **soft margin.**
	![[Pasted image 20230901130346.png]]
The best hyperplane is that plane that has the maximum distance from both the classes, and this is the main aim of SVM. This is done by finding different hyperplanes which classify the labels in the best way then it will choose the one which is farthest from the data points or the one which has a maximum margin.
#### Summary

- Consider a random point X and we want to know whether it lies on the right side of the plane or the left side of the plane (positive or negative).
	![[Pasted image 20230901130635.png]]
- To find this first we assume this point is a vector (X) and then we make a vector (w) which is perpendicular to the hyperplane. Let’s say the distance of vector w from origin to decision boundary is ‘c’. Now we take the projection of X vector on w.
	![[Pasted image 20230901130746.png]]
- Hence, we take the dot product of x and w vectors. If the dot product is greater than ‘c’ then we can say that the point lies on the right side. If the dot product is less than ‘c’ then the point is on the left side and if the dot product is equal to ‘c’ then the point lies on the decision boundary.
	![[Pasted image 20230901130820.png]]
	or
	![[Pasted image 20230901134858.png]]
	If the value of w.x+b>0 then we can say it is a positive point otherwise it is a negative point. Now we need (w,b) such that the margin has a maximum distance. Let’s say this distance is ‘d’.
	![[Pasted image 20230901134947.png]]
	Now the question comes
	1. Why the magnitude is equal, why didn’t we take 1 and -2?
	2. Why did we only take 1 and -1, why not any other value like 24 and -100?
	3. Why did we assume this line?
	Let’s try to answer these questions
	1. We want our plane to have equal distance from both the classes that means L should pass through the centre of L1 and L2 that’s why we take magnitude equal.
	2. Let’s say the equation of our hyperplane is 2x+y=2, we observe that even if we multiply the whole equation with some other number the line doesn’t change (try plotting on a graph). Hence for mathematical convenience, we take it as 1.
	3. Now the main question is exactly why there’s a need to assume only this line? To answer this, I’ll try to take the help of graphs.
#### **Optimization** F**unction and its Constraints** for Hard Margin SVM
- In order to get our optimization function, there are few constraints to consider. That constraint is that **“We’ll calculate the distance (d) in such a way that no positive or negative point can cross the margin line”.** Let’s write these constraints mathematically:
	![[Pasted image 20230901135140.png]]
	Rather than taking 2 constraints forward, we’ll now try to simplify these two constraints into 1. We assume that negative classes have _**y=-1**_ and positive classes have **_**y=1**._**
	We can say that for every point to be correctly classified this condition should always be true:
	![[Pasted image 20230901135242.png]]
	Suppose a green point is correctly classified that means it will follow **w.x+b>=1,** if we multiply this with **y=1** we get this same equation mentioned above. Similarly, if we do this with a red point with **y=-1** we will again get this equation**.** Hence, we can say that we need to maximize (d) such that this constraint holds true.
	We will take 2 support vectors, 1 from the negative class and 2nd from the positive class. The distance between these two vectors x1 and x2 will be _(x2-x1) vector_. What we need is, the shortest distance between these two points which can be found using a trick we used in the dot product. We take a vector ‘w’ perpendicular to the hyperplane and then find the projection of (x2-x1) vector on ‘w’. **Note:** this perpendicular vector should be a unit vector then only this will work. Why this should be a unit vector? To make this ‘w’ a unit vector we divide this with the norm of ‘w’.
	![[Pasted image 20230901135454.png]]
	Lets find the projection of  x1-x2 to w:
	![[Pasted image 20230901135603.png]]
	Since x2 and x1 are support vectors and they lie on the hyperplane, hence they will follow **yi* (2.x+b)=1** so we can write it as:
	![[Pasted image 20230901135645.png]]
	Putting equations (2) and (3) in equation (1) we get:
	![[Pasted image 20230901135710.png]]
	Hence the equation which we have to maximize is:
	![[Pasted image 20230901135943.png]]
	`argmax( 2 / ||W||) where we are seraching for w and b for all i such that Yi(W^T * Xi+b)>= 1`
	We have now found our optimization function but there is a catch here that we don’t find this type of perfectly linearly separable data in the industry, there is hardly any case we get this type of data and hence we fail to use this condition we proved here. The type of problem which we just studied is called **Hard Margin SVM**
#### Soft Margin SVM
- In real-life applications we don’t find any dataset which is linearly separable, what we’ll find is either an almost linearly separable dataset or a non-linearly separable dataset. In this scenario, we can’t use the trick we proved above because it says that it will function only when the dataset is perfectly linearly separable.
  To tackle this problem what we do is modify that equation in such a way that it allows few misclassifications that means it allows few points to be wrongly classified.
  We know that _max[f(x)]_ can also be written as _min[1/f(x)]_, it is common practice to minimize a cost function for optimization problems; therefore, we can invert the function.
  ![[Pasted image 20230901142912.png]]
  To make a soft margin equation we add 2 more terms to this equation which is **zeta** and multiply that by a **hyperparameter ‘c’**
  ![[Pasted image 20230901142923.png]]
  Since its more convenient to minimize the quadratic function, sometimes we can re-write upper formula as follows: 
  ![[Pasted image 20230901150211.png]]
  For all the **_correctly classified_** points our **zeta** will be equal to 0 and for all the **_incorrectly classified_** points the **zeta** is simply the distance of that particular point from its correct hyperplane that means if we see the wrongly classified green points the value of **zeta** will be the distance of these points from L1 hyperplane and for wrongly classified redpoint **zeta** will be the distance of that point from L2 hyperplane. We're doing this in order to introduce the penalty term in our equation
  ![[Pasted image 20230901143059.png]]
  
  So now we can say that our that are **SVM Error = Margin Error + Classification Error.** The higher the margin, the lower would-be margin error, and vice versa.
  Let’s say you take a high value of ‘c’ =1000, this would mean that you don’t want to focus on margin error and just want a model which doesn’t misclassify any data point.
**The Role of the Hyperparameter 'C'**: The hyperparameter 'C' in SVM represents the regularization strength. It controls the trade-off between margin error and classification error.
- **High 'C' Value (e.g., 1000)**: When you set 'C' to a high value like 1000, it means you are placing a strong emphasis on minimizing classification error. In other words, you are telling the SVM that you want a model that tries its best to correctly classify every data point, even if it means accepting a narrower margin. This is often used when you want a very strict and precise classification.
- **Low 'C' Value (e.g., 0.001)**: Conversely, when 'C' is set to a low value, it indicates a preference for a wider margin, even if it results in some classification errors. The SVM is allowed to have a larger margin, which can lead to a more robust model against outliers and noisy data, even if it means tolerating some misclassifications.