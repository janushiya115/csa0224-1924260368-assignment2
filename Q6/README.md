
#include <stdio.h>

int main()
{
    double principal, rate, repayment;
    double balance, interest, totalInterest = 0;
    double due, payment;
    int month = 0;

    printf("Enter loan amount: ");
    scanf("%lf", &principal);

    printf("Enter monthly interest rate: ");
    scanf("%lf", &rate);

    printf("Enter monthly repayment: ");
    scanf("%lf", &repayment);

    if(principal <= 0 || rate < 0 || repayment <= 0)
    {
        printf("Invalid input\n");
        return 0;
    }

    balance = principal;

    if(repayment <= balance * rate / 100)
    {
        printf("Repayment is too small. Loan cannot decrease.\n");
        return 0;
    }

    printf("\nMonth\tInterest\tPayment\t\tBalance\n");

    while(balance > 0.005)
    {
        if(month >= 360)
        {
            printf("\nSafety limit reached. Loan not fully repaid.\n");
            break;
        }

        interest = balance * rate / 100;
        totalInterest += interest;

        due = balance + interest;

        if(repayment < due)
            payment = repayment;
        else
            payment = due;

        balance = due - payment;

        if(balance < 0.005)
            balance = 0;

        month++;

        printf("%d\t%.2f\t\t%.2f\t\t%.2f\n",
               month, interest, payment, balance);
    }

    if(balance == 0)
    {
        printf("\nLoan fully repaid!\n");
        printf("Total months = %d\n", month);
        printf("Total interest = Rs. %.2f\n", totalInterest);
    }

    return 0;
}

