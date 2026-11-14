
#include <stdio.h>

int main()
{
    float price, gross, discount, gst, total, net;
    int qty, senior, count = 0, i;

    for(i = 1; i <= 3; i++)
    {
        printf("\nEnter price: ");
        scanf("%f", &price);

        printf("Enter quantity: ");
        scanf("%d", &qty);

        printf("Senior citizen? (1=Yes, 0=No): ");
        scanf("%d", &senior);

        gross = price * qty;

        if(senior == 1)
            discount = gross * 15 / 100;
        else
            discount = 0;

        gst = (gross - discount) * 5 / 100;

        total = gross - discount + gst;

        if(total > 1000)
            net = total - 50;
        else
            net = total;

        count++;

        printf("Gross Amount = Rs. %.2f\n", gross);
        printf("Discount = Rs. %.2f\n", discount);
        printf("GST = Rs. %.2f\n", gst);
        printf("Final Amount = Rs. %.2f\n", net);
    }

    printf("\nTotal Bills = %d\n", count);

    return 0;
}

