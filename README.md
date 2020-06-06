# calculator
Basic operations 


#include <iostream>
#include <iomanip>


using namespace std;

int main()
{
	char again;
	int a, b, answer, guess;
	int options = 0;
	int correct = 0;
	int incorrect = 0;
	int tasks = 0;
	float percent;
	char goodAnswers[4][12] =
	{
		{ "Excellent!" },
		{ "Good Job!" },
		{ "Keep going!" },
		{ "Master!" }
	};
	char badAnswers[4][20] =
	{
		{"Try again!"},
		{"Don't give up!"},
		{"Keep trying!"},
		{"Try one more time!"}
	};
	tasks = incorrect + correct;

	cout << "Welcome. Are you ready? Type 'y'." << endl;
	again = 'Y';
	cin >> again;
	while (tasks <= 10)
	{
		srand(time(NULL));
		a = rand() % 9 + 1;
		b = rand() % 9 + 1;

		cout << "How much is " << a << " times " << b << "?" << endl;
		cin >> guess;
		answer = a * b;

		while (answer != guess) 
		{
			incorrect++;
			cout << badAnswers[rand() %4] << endl;
			cout << "How much is " << a << " times " << b << "?" << endl;
			cin >> guess;	
		}
			cout << goodAnswers[rand() % 4] << endl;	
			correct++;
	}
	
	percent = correct / tasks;
	if (percent < 0.75)
	{
		cout << "Please ask your teacher for extra help.";
		return 0;
	}
	else 
		cout << "Congratulations, you are ready to go to the next level! Type 'y'." << endl;
	cin >> again;
	guess = -1;
	while ((again == 'y') || (again == 'Y'))
	{
	    srand(time(NULL));
    	a = rand() % 99 + 1;
    	b = rand() % 99 + 1;
    	while (options < 1 || options > 4)
       	{
	    	cout << "Choose an option - an integer between 1 and 4." << endl;
		    cin >> options;
    	}
	switch (options)
	{
	case 1: '+';
		cout << "How much is" << a << " plus " << b << "?" << endl;
		answer = a + b;
		cin >> guess;
		break;
	case 2: '-';
		cout << "How much is" << a << " minus " << b << "?" << endl;
		answer = a - b;
		cin >> guess;
		break;
	case 3: '*';
		cout << "How much is " << a << " times " << b << "?" << endl;
		answer = a * b;
		cin >> guess;
		break;
	case 4: '/';
		cout << "How much is " << a << " divided " << b << "?" << endl;
		answer = a / b;
		cin >> guess;
		break;
	}
	while (answer != guess)
		{
			cout << badAnswers[rand() %4] << endl;
			cin >> guess;
		}
		
		cout << goodAnswers[rand() % 4] << endl;
		cout << "Choose another option. Type 'y'." << endl;
		cin >> again;
	}
	

	return 0;
}



