# PullDataCAFCI
The code pulls and organices data available through the public CAFCI API

## Development

Libraries used to manipulate the data and the API:

> json
> requests  
> os
> pandas
> time

## The code

The Argentinean mutual funds chamber has developed an API that makes public the portfolio allocations of every exiting fund on a daily basis. However, in order to be able to manipulate the data and make it useful for the end user it is necesary to take some additional steps in between. 

The API shows every invididual portfolio in an individual endpoint, each ending in a chain of numbers that are not related to the valuation date nor the funds'name or the asset management company. If there is another portfolio available, the end number in the endpoint increases by one. This issue has to be addressed not only to guarantee that the data will be available in the future but also to help the user to keep track of the data avalilable through the API.

One way to address this problem was to both download the data and save it in an individual json file, one for each date. Moreover, the code also keeps track of the dates (days_list.json) already available and creates a new json file when a new date is available. The code will also notify that there is not more data available by checking the status code. Since the endponit number will be necessary to continue the download process once there is new data available, the code saves this number in another json file (start_fund.json). 

Last but not least, sometimes mutual fund companies review the daily NAV published days before. In order to address this time gap, the code saves the last day of data available (last_day.json) and compares it with the current being downloaded. This way, the new data will be saved in the correct file named after the correct date.


## Results

Once there is no more data available the code stops looping. The user should be aware that the chamber usually makes data public stating at 2 pm ET.

<ipython-input-16-65fbde99536e> in <module>
----> 1 while (status_code == 200 and data["success"]):
      2 
      3     cartera , fecha_fondo , nombre_fondo = get_portfolio(data)
      4     print(fund , fecha_fondo)
      5 

KeyError: 'success'




