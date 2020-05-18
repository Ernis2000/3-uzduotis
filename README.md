# 3 užduotis

# Funkcijų pavyzdžiai

- Swap - apkeičia reikšmes vietomis
```
template<typename T>
void Vector<T>::swap(Vector<T>& v)
{
    iterator data2 = data1, avail2 = avail, limit2 = limit;
    data1 = v.data1;
    limit = v.limit;
    avail = v.avail;

    v.data1 = data2;
    v.avail = avail2;
    v.limit = limit2;
}
```
- Clear - pašalina visus elementus iš vektoriaus, paliekant vektoriaus dydį lygų nuliui
```
template <typename T>
void Vector<T>::clear()
{
    resize(0);
}
```
- Shrink_to_fit - sumažina konteinerio talpą, kad ji būtų tokia kaip ir elementų skaičius
```
template <typename T>
void Vector<T>::shrink_to_fit()
{
    if (avail < limit)
    {
        limit = avail;
    }
}
```
- Operator == - lygina ar reikšmės yra vienodos
```
template<typename T>
bool Vector<T>::operator==(const Vector<T>& v) const
{
    if (v.size() != size())
        return false;

    else
    {
        int g = v.size();

        for (int k = 0; k < g; k++)
        {
            if (data1[k] != v.data1[k]) { return false; }
        }

        return true;
    }
}
```
- Resize - pakeičia konteinerio dydį, kad jame tilptų n elementų
```
template <typename T>
void Vector<T>::resize(int n)
{
    int k = 0;
    if (n < size())
    {
        for (int i = n; i < size(); i++)
        {
            data1[i] = 0;
            k++;
        }
        avail -= k;
    }

    else
    {
        int o = size();
        int z = n - size();
        avail += z;

        for (int i = o; i < n; i++)
        {
            data1[i] = 0;
        }
    }
}
```
# Spartos analizė

| Konteineris | 10000 | 100000 | 1000000 | 10000000 | 100000000 |
