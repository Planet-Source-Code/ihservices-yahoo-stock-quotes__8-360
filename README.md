<div align="center">

## Yahoo stock quotes


</div>

### Description

Displays stock quotes from yahoo on your site .
 
### More Info
 
Someone sent this to my email , too good not too share with others . A slightly better version with user input and tidier output can be found at http://www.mywebresources.co.uk/php/quotes.htm

Good news on your stocks hopefully :-)

You have to change the MSFT in the line $quote->get_stock_quote("MSFT"); to whatever ticker symbol you wish unless you only wish Microsoft.

e.g SUN , FORD


<span>             |<span>
---                |---
**Submitted On**   |
**By**             |[ihservices](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByAuthor/ihservices.md)
**Level**          |Beginner
**User Rating**    |4.3 (17 globes from 4 users)
**Compatibility**  |PHP 3\.0, PHP 4\.0
**Category**       |[Internet/ Browsers/ HTML](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByCategory/internet-browsers-html__8-9.md)
**World**          |[PHP](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByWorld/php.md)
**Archive File**   |[](https://github.com/Planet-Source-Code/ihservices-yahoo-stock-quotes__8-360/archive/master.zip)





### Source Code

```
<?php
Class yahoo
{
function get_stock_quote($symbol)
{
$url = sprintf("http://finance.yahoo.com/d/quotes.csv?s=%s&f=sl1d1t1c1ohgv" ,$symbol);
$fp = fopen($url, "r");
if(!fp)
{
echo "error : cannot recieve stock quote information";
}
else
{
$array = fgetcsv($fp , 4096 , ', ');
fclose($fp);
$this->symbol = $array[0];
$this->last = $array[1];
$this->date = $array[2];
$this->time = $array[3];
$this->change = $array[4];
$this->open = $array[5];
$this->high = $array[6];
$this->low = $array[7];
$this->volume = $array[8];
}
}
}
$quote = new yahoo;
$quote->get_stock_quote("MSFT");
echo ("<B>$quote->symbol</B><br>");
echo ("<B>$quote->time</B><br>");
echo ("<B>$quote->date</B><br>");
echo ("<B>$quote->last</B><br>");
echo ("<B>$quote->change</B><br>");
echo ("<B>$quote->high</B><br>");
echo ("<B>$quote->low</B><br>");
?>
```

