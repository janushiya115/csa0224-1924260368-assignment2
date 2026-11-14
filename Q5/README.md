

#include <stdio.h>

unsigned long checks = 0;

// Normal method
int normal_prime(unsigned long n)
{
    checks = 0;

    if(n < 2)
        return 0;

    for(unsigned long i = 2; i < n; i++)
    {
        checks++;

        if(n % i == 0)
            return 0;
    }

    return 1;
}

// Improved for loop
int prime_for(unsigned long n)
{
    checks = 0;

    if(n < 2)
        return 0;

    for(unsigned long i = 2; i <= n / i; i++)
    {
        checks++;

        if(n % i == 0)
            return 0;
    }

    return 1;
}

// Improved while loop
int prime_while(unsigned long n)
{
    checks = 0;

    if(n < 2)
        return 0;

    unsigned long i = 2;

    while(i <= n / i)
    {
        checks++;

        if(n % i == 0)
            return 0;

        i++;
    }

    return 1;
}

// Improved do-while loop
int prime_do(unsigned long n)
{
    checks = 0;

    if(n < 2)
        return 0;

    unsigned long i = 2;

    if(i <= n / i)
    {
        do
        {
            checks++;

            if(n % i == 0)
                return 0;

            i++;

        } while(i <= n / i);
    }

    return 1;
}

int main()
{
    unsigned long tickets[] = {97, 100, 7919, 1000003};

    for(int k = 0; k < 4; k++)
    {
        int p = normal_prime(tickets[k]);

        printf("%lu Normal: %s, divisions = %lu\n",
               tickets[k], p ? "prime" : "not prime", checks);

        p = prime_for(tickets[k]);

        printf("%lu For: %s, divisions = %lu\n",
               tickets[k], p ? "prime" : "not prime", checks);

        p = prime_while(tickets[k]);

        printf("%lu While: %s, divisions = %lu\n",
               tickets[k], p ? "prime" : "not prime", checks);

        p = prime_do(tickets[k]);

        printf("%lu Do-while: %s, divisions = %lu\n\n",
               tickets[k], p ? "prime" : "not prime", checks);
    }

    return 0;
}
