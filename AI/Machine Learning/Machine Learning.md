- ML algorithms are classified into **Three** types
	- Supervised Learning
	- Unsupervised Learning
	- Semi-Supervised Leaning
	- Reinforcement Learning
- Supervised Learning
	 Supervised learning uses a training set to teach models to yield the desired output. This training dataset includes inputs and correct outputs, which allow the model to learn over time. 
					- ![[Pasted image 20231205233240.png]]
	  In this case, we have images that are labeled a spoon or a knife. This known data is fed to the machine, which analyzes and learns the association of these images based on its features such as shape, size, sharpness, etc. Now when a new image is fed to the machine without any label, the machine is able to predict accurately that it is a spoon with the help of the past data. 
	  - Real-Life Applications of Supervised Learning
		  - Risk Assessment
		  - Image Classification
		  - Fraud Detection
		  - Visual Recognition
	 There are two types of Supervised Learning technics
			 1. Regression
			 2. Classification
	 - Regression
		 - Regression is used when the output variable is a real or continuous value. In this case, there is a relationship between two or more variables i.e., a change in one variable is associated with a change in the other variable. For example, salary based on work experience or weight based on height, etc.
		 - ![[Pasted image 20231206174807.png]]
		 - Let’s consider two variables - humidity and temperature. Here, ‘temperature’ is the independent variable and ‘humidity' is the dependent variable. If the temperature increases, then the humidity decreases. 
		 - These two variables are fed to the model and the machine learns the relationship between them. After the machine is trained, it can easily predict the humidity based on the given temperature.
	 - Classification
		 - Classification is used when the output variable is categorical i.e. with 2 or more classes. For example, yes or no, male or female, true or false, etc.
		 - In short, classification is a form of “pattern recognition,” with classification algorithms applied to the training data to find the same pattern (similar words or sentiments, number sequences, etc.) in future sets of data.
		 - Popular Classification algorithms
			 - Logistic Regression
			 - Naive Bayes
			 - K-Nearest Neighbors
			 - Decision Tree
			 - Support vector Machines
		- Applications using classification algorithms
			- Sentiment Analysis
			- Email spam Classification
			- Document Classification
			- Image Classification
			 ![[Pasted image 20231205233626.png]]
		- In order to predict whether a mail is spam or not, we need to first teach the machine what a spam mail is. This is done based on a lot of spam filters - reviewing the content of the mail, reviewing the mail header, and then searching if it contains any false information. Certain keywords and blacklist filters that blackmails are used from already blacklisted spammers.
		- All of these features are used to score the mail and give it a spam score. The lower the total spam score of the email, the more likely that it is not a scam

- Unsupervised Learning
	- In Unsupervised Learning, the machine uses unlabeled data and learns on itself without any supervision. The machine tries to find a pattern in the unlabeled data and gives a response.
		![[Pasted image 20231206181207.png]]
		Let's take a similar example is before, but this time we do not tell the machine whether it's a spoon or a knife. The machine identifies patterns from the given set and groups them based on their patterns, similarities, etc.
	 - Real-Life Applications of Unsupervised Learning
		 - Market Basket Analysis
		 - Semantic Clustering
		 - Delivery Store Optimization
		 - Identifying Accident Prone Areas
	 - Unsupervised learning can be further grouped into types:
				 - Clustering
				 - Association
	 - Clustering
		 - Clustering is the method of dividing the objects into clusters that are similar between them and are dissimilar to the objects belonging to another cluster. For example, finding out which customers made similar product purchases.
		 - ![[Pasted image 20231206181517.png]]
		 - Suppose a telecom company wants to reduce its customer churn rate by providing personalized call and data plans. The behavior of the customers is studied and the model segments the customers with similar traits. Several strategies are adopted to minimize churn rate and maximize profit through suitable promotions and campaigns.
		 - On the right side of the image, you can see a graph where customers are grouped. Group A customers use more data and also have high call durations. Group B customers are heavy Internet users, while Group C customers have high call duration. So, Group B will be given more data benefit plants, while Group C will be given cheaper called call rate plans and group A will be given the benefit of both.
	- Association
		- Association is a rule-based machine learning to discover the probability of the co-occurrence of items in a collection. For example, finding out which products were purchased together.
		- ![[Pasted image 20231206181815.png]]
		- Let’s say that a customer goes to a supermarket and buys bread, milk, fruits, and wheat. Another customer comes and buys bread, milk, rice, and butter. Now, when another customer comes, it is highly likely that if he buys bread, he will buy milk too. Hence, a relationship is established based on customer behavior and recommendations are made.
- 



	Supervised Learning Algorithms
		- Regression
			- Ordinary Least Square Regression
			- Simple Linear Regression
			- Multiple Linear Regression
			- Least-angle regression (LARS)
			- Stepwise regression
			- Isotonic regression
			- Quantile Regression
		- Classification
			- Logistic Regression
			- Sigmoid & Softmax functions
- Unsupervised learning
- Semi-Supervised leaning
- Reinforcement learning