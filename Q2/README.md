
#include <stdio.h>

int calls = 0;

int verifyCard(int card)
{
    calls++;
    return card;
}

int main()
{
    int i, senior, eligible, card;

    // Experiment 1
    calls = 0;

    for(i = 0; i < 1000; i++)
    {
        senior = (i < 300);
        eligible = (i < 200);
        card = (i % 10 == 0);

        if((senior && eligible) || verifyCard(card))
        {
        }
    }

    printf("Order 1 calls = %d\n", calls);

    // Experiment 2
    calls = 0;

    for(i = 0; i < 1000; i++)
    {
        senior = (i < 300);
        eligible = (i < 200);
        card = (i % 10 == 0);

        if(verifyCard(card) || (senior && eligible))
        {
        }
    }

    printf("Order 2 calls = %d\n", calls);

    // Experiment 3
    calls = 0;

    for(i = 0; i < 1000; i++)
    {
        senior = (i < 300);
        card = (i % 10 == 0);

        if(senior & verifyCard(card))
        {
        }
    }

    printf("Bitwise AND calls = %d\n", calls);

    return 0;
}

