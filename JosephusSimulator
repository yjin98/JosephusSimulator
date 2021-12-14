#include <iostream>
#include <vector>
#include <ctime>
#include <cstdlib>

using namespace std;

struct mem {
    int m;
    mem* pr = 0;
    mem* ne = 0;
};

struct R {
    vector<int> v;
    clock_t T;
};

R Jlink(int, int);
R Jpoint(int, int);

int main()
{
    
    int n, k;
    cout << "Enter the number of members\n";
    cin >> n;
    cout << "Enter the count\n";
    cin >> k;
    
    R rep;

    rep = Jpoint(n, k);
    
    for (int i = 0; i < n; i++)
    {
        cout << rep.v[i] << "  ";
    }

    return 0;
}

R Jlink(int n, int k)
{
    R re;

    clock_t T0 = clock();
    vector<int> t(n);
    int i = 0;
    while (i < n - 1)
    {
        t[i] = i + 1;
        i = i + 1;
    }
    t[n - 1] = 0;

    i = 0;
    int c = 1, p = 0, p0 = 0;
    while (i < n - 1)
    {
        while (c < k)
        {
            p0 = p;
            p = t[p];
            c = c + 1;
        }
        re.v.push_back(p + 1);
        p = t[p];
        t[p0] = p;
        i = i + 1;
        c = 1;
    }
    re.v.push_back(p + 1);
    re.T = clock() - T0;

    return re;
}

R Jpoint(int n, int k) //
{
    R re;

    clock_t T0 = clock();
    mem* t, * p = 0, * p0 = 0;
    t = new mem;
    p = t;
    t->m = 1;
    t->ne = 0;
    t->pr = 0;
    for (int i = 2; i < n; i++)
    {
        p->ne = new mem;
        p->ne->pr = p;
        p->ne->ne = 0;
        p = p->ne;
        p->m = i;
    }
    p->ne = new mem;
    p->ne->pr = p;
    p->ne->ne = t;
    p = p->ne;
    p->m = n;
    t->pr = p;
    p = t;

    int c = 1, i = 1;
    while (i < n)
    {
        while (c < k)
        {
            p = p->ne;
            c = c + 1;
        }
        re.v.push_back(p->m);
        p->pr->ne = p->ne;
        p->ne->pr = p->pr;
        p0 = p;
        p = p->ne;
        p0->pr = 0;
        p0->ne = 0;
        free(p0);
        p0 = 0;
        i = i + 1;
        c = 1;
    }
    re.v.push_back(p->m);
    re.T = clock() - T0;

    return re;
}
