## Welcome to My sample loan calculator in C

You can use the [editor on GitHub](https://github.com/milicmil/MscPortfolio/edit/master/index.md) to maintain and preview the content for your website in Markdown files.

Whenever you commit to this repository, GitHub Pages will run [Jekyll](https://jekyllrb.com/) to rebuild the pages in your site, from the content in your Markdown files.

### Markdown

This is a small program which is a mortgage calculaor written in C. There are three Inputs. The Loan Amount, The number of months requred to pay off and the annual interest rate. The calculator will print out the outputs of the Months as they count down to 0, cumulative interest and the amount owing at the end of the month. The program uses a recursive method to complete the cycle. 

```markdown
Syntax highlighted code block


#include <stdio.h>
#include <stdlib.h>
#include <stdbool.h>
#include <ctype.h>
#include <math.h>

typedef struct UserValues UserValues;     // shorthand name for user values

int max;   //Variable 

struct UserValues {                    // defining userValues structure
    
    float ratepaid;
    float amount;
    float monthamount;
    float principal;
    float rate;
    int payments;
    float finalrate;
    float monthrate;
};

UserValues *pUser;              // defining a global pointer to access values


/**
 * The MonthlyPayment() accepts the user's payment period as the variable 
 * to drive the recursive calculations of the Mortgage Calculator
 * 
 * @param payments The UserValues struct data member field: payments
 * 
 * @return * @return A recursive call to the MonthlyPayment() function
 */
int MonthlyPayment(int i) {
    
    if (i < (max) ) {
	
        // The initial Mortgage calculation.
        pUser->amount = pow(pUser->finalrate, i) * pUser->principal - ((pow(pUser ->finalrate, i)-1 ) / 
                (pUser ->monthrate) * pUser ->monthamount);
	
        pUser->ratepaid = (((pUser->principal * pUser->monthrate  - pUser->monthamount) * ((pow(pUser->finalrate, i) - 1) / 
                (pUser->monthrate))) + (pUser->monthamount * i) );
        /**
         * Print the initial Amount Owed
         * Print the payment month in question..
         * Print the Interest Amount
        **/
        printf("\nAmount Owing: $%10.2f\tThe payment month: %d\tCumulative Interest Amount: $%10.2f\n", 
                pUser->amount,
                (i),
                (pUser->ratepaid));
        
        return MonthlyPayment(i + 1);  // add 1 from argument 'payments'
    }
    else  {
        return (max);  // The Base Case!
    }
    
}


int main(void) {
    printf("\n\n");         // cosmetic separation spaces

    
    UserValues user;        // UserValues structure declaration
    pUser = &user;          
    char test = '\0';       // test variable declared


    /**
    * Asking if user would like to use the program; setting a test to exit
    **/
    printf("Would you like to use the Loan Payback Period Calculator (y OR n): ");
    scanf("%c", &test);

    while (tolower(test) == 'n') {

        if (!(test == 'y')) {
            printf("Thank You\n\n");
            exit(0);
      	}
    }

    
    /**
    * Setting the user's values for interest rate, payback months, and principal
    **/
    printf("Enter loan's interest rate (eg.. 4.5, 10.0, 1.4): ");
    scanf("%f", &user.rate);

    printf("Enter the required months for the payback period: ");
    scanf("%d", &user.payments);
    
    max = user.payments+1;
    
    /**
     * Storing the principal amount in another variable 
     * previousPrincipal, as well..
     */
    printf("What is the principal amount $");
    scanf("%f", &user.principal);
    
    printf("\n\nThe Principal $%.2f\nThe Rate: %.2f percent\nThe Payback Period: %d\n",
    user.principal, user.rate, user.payments);
    
    user.finalrate = 1+(user.rate/12/100);
    printf("The monthly rate is %.4f\n ", user.finalrate);
    user.monthrate = user.rate/12/100;

    user.monthamount = user.monthrate*user.principal/(1- pow(user.finalrate,user.payments*-1));
    printf("\n\nThe Monthly Payment Amount is $%.2f\n\n ", user.monthamount);
    
    MonthlyPayment(user.payments-user.payments+1); 

    
    printf("\n\n");               // cosmetic separation spaces
    return 0;

}



[Link](url) and ![Image](src)
```

For more details see [GitHub Flavored Markdown](https://guides.github.com/features/mastering-markdown/).

### Jekyll Themes

Your Pages site will use the layout and styles from the Jekyll theme you have selected in your [repository settings](https://github.com/milicmil/MscPortfolio/settings). The name of this theme is saved in the Jekyll `_config.yml` configuration file.

### Support or Contact

Having trouble with Pages? Check out our [documentation](https://help.github.com/categories/github-pages-basics/) or [contact support](https://github.com/contact) and we’ll help you sort it out.
