# django-prices-vatlayer
[Vatlayer API](https://vatlayer.com/) support for django-prices

```python
from prices import Price
from django_prices_vatlayer.european_vat import get_price_with_vat

price_with_vat = get_price_with_vat('SK', Price(10, currency='USD'))
print(price_with_vat)
# Price(net='10', gross='12', currency='USD')
print(price_with_vat.history)
# (Price('10', currency='USD') | EuropeanVat(SK, None))
```

Installation
==============
First install the package:
```
pip install django-prices-vatlayer
```
Then add `'django_prices_vatlayer'` to your `INSTALLED_APPS`.

Set following settings in your project's settings:

 * `VATLAYER_ACCESS_KEY`


Update vat rates
=======================
Fetch current vat rates from API with `./manage.py get_vat_rates`

Schedule this task in cron job or in celery, to be always up to date with exchange rates
