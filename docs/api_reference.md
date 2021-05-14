Module py_exchangeratesapi
==========================

Classes
-------

## `Api(api_key=None)`
ExchangeRatesApi Client. if api_key is None, then EXCHANGERATESAPI_KEY
environment variable would be used.
    
### Class variables

`Api.supported_currencies`: tuple of supported currencies

### Methods

### `Api.convert(amount, base, target, date=None)`
Method to convert a given amount of a currency
to another on a given date or latest.

**Args**:
* amount (int/float): amount to convert
* base (str): 3-letter currency code
* target (str): 3-letter currency code
* date (str): date string in format YYYY-MM-DD

**Returns** (float): converted amount

**Examples**:
```python
>>> api.convert(10, 'EUR', 'USD')
11.9655

>>> api.convert(25, 'USD', 'EUR', '2014-03-26')
18.13265
```

### `Api.fluctuation(base='EUR', target=None, start_date=None, end_date=None)`
Method to get currency's change parameters (margin and percentage),
optionally between two specified dates.

**Args**:
* base (str): 3-letter currency code
* target (str/list): 3-letter currency code or list of 
    3-letter currency code
* start_date (str): date string in format YYYY-MM-DD
* end_date (str): date string in format YYYY-MM-DD

**Returns** (dict): fluctuation

### `Api.get_rate(base='EUR', target='USD', start_date=None, end_date=None)`
Method to get exchange rate for a given currency
against a target.

**Args**:
* base (str): 3-letter currency code, default 'EUR'
* target (str): 3-letter currency code
* start_date (str): date string in format YYYY-MM-DD
* end_date (str): date string in format YYYY-MM-DD

**Returns** (float): currency rate

**Examples**:
```python
>>> api.get_rate()
394.55

>>> api.get_rate('USD', 'EUR', start_date="2019-09-12")
0.897
```

### `Api.get_rates(base=None, target_list=[], start_date=None, end_date=None)`
Method to get exchange rates for a given currency
against multiple targets.

**Args**:
* base (str): 3-letter currency code
* target_list (str): list of 3-letter currency codes
* start_date (str): date string in format YYYY-MM-DD
* end_date (str): date string in format YYYY-MM-DD

**Returns** (float): currency rate

**Examples**:
```python
>>> api.get_rates()
...

>>> api.get_rates('USD', ['EUR','CAD','GBP'],
                  start_date="2019-09-12")
...
```

### `Api.is_currency_supported(currency)`
Method to check if currency is supported.

**Args**:
* currency (str): 3-letter currency code

**Returns** (bool): if currency is supported

## `ExchangeRatesApiException`
Custom Exception
