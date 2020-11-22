# Plug DREMIO Data Lake Driver into Jupyter Notebooks

## Standalone Container

Setup
```python
import pandas as pd 
import pyodbc
import credentials # separate file with user credentials
```

Pyodbc settings
```python
host = 'localhost'
port = 31010
uid = credentials.user
pwd = credentials.password
driver = '/opt/dremio-odbc/lib64/libdrillodbc_sb64.so'
cnxn = pyodbc.connect("Driver={};ConnectionType=Direct;HOST={};PORT={};AuthenticationType=Plain;UID={};PWD={};".format(driver, host, port, uid, pwd), autocommit=True)
```

Read dataframe based on SQL Query
```python
sql = 'SELECT * from "test"."weather" Limit 10'
df = pd.read_sql(sql, cnxn)
```

Output
```python
df.head()
```

<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>STATION</th>
      <th>NAME</th>
      <th>LATITUDE</th>
      <th>LONGITUDE</th>
      <th>ELEVATION</th>
      <th>DATE</th>
      <th>PRCP</th>
      <th>SNOW</th>
      <th>SNWD</th>
      <th>TAVG</th>
      <th>TMAX</th>
      <th>TMIN</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>USW00023272</td>
      <td>SAN FRANCISCO DOWNTOWN, CA US</td>
      <td>37.7705</td>
      <td>-122.4269</td>
      <td>45.7</td>
      <td>2018-01-01</td>
      <td>0.00</td>
      <td></td>
      <td></td>
      <td></td>
      <td>61</td>
      <td>48</td>
    </tr>
    <tr>
      <th>1</th>
      <td>USW00023272</td>
      <td>SAN FRANCISCO DOWNTOWN, CA US</td>
      <td>37.7705</td>
      <td>-122.4269</td>
      <td>45.7</td>
      <td>2018-01-02</td>
      <td>0.00</td>
      <td></td>
      <td></td>
      <td></td>
      <td>61</td>
      <td>52</td>
    </tr>
    <tr>
      <th>2</th>
      <td>USW00023272</td>
      <td>SAN FRANCISCO DOWNTOWN, CA US</td>
      <td>37.7705</td>
      <td>-122.4269</td>
      <td>45.7</td>
      <td>2018-01-03</td>
      <td>0.09</td>
      <td></td>
      <td></td>
      <td></td>
      <td>58</td>
      <td>53</td>
    </tr>
    <tr>
      <th>3</th>
      <td>USW00023272</td>
      <td>SAN FRANCISCO DOWNTOWN, CA US</td>
      <td>37.7705</td>
      <td>-122.4269</td>
      <td>45.7</td>
      <td>2018-01-04</td>
      <td>0.06</td>
      <td></td>
      <td></td>
      <td></td>
      <td>63</td>
      <td>53</td>
    </tr>
    <tr>
      <th>4</th>
      <td>USW00023272</td>
      <td>SAN FRANCISCO DOWNTOWN, CA US</td>
      <td>37.7705</td>
      <td>-122.4269</td>
      <td>45.7</td>
      <td>2018-01-05</td>
      <td>0.26</td>
      <td></td>
      <td></td>
      <td></td>
      <td>61</td>
      <td>52</td>
    </tr>
  </tbody>
</table>
</div>

## Requirements
- [Docker](https://docs.docker.com/get-docker/)
- Venv or Conda environment
- [Pip](https://pip.pypa.io/en/stable/installing/)
- [Dremio Data Lake Standalone](https://docs.dremio.com/quickstart/standalone-quickstart.html) Community or Enterprise Edition
- [Dremio ODBC compatible driver](https://www.dremio.com/drivers/)
- [Python package requirements](./requirements.txt)

### References

*DREMIO - The Data Lake Engine [docs](https://docs.dremio.com/).*
