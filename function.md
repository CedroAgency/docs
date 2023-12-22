```php
use Bitrix\Highloadblock as HL;
use Bitrix\Main\Entity;
function na($param)
{
	global $USER;
	if ($USER->IsAdmin()) {
		echo '<pre style="color:#000;background:#fff">';
		print_r($param);
		echo '</pre>';
	}
}

function cho($param)
{
	global $USER;
	if ($USER->IsAdmin())
	{
		echo '<pre style="color:#000;background:#fff">';
		var_dump($param);
		echo '</pre>';
	}
}

function is_arr($v)
{
	return ($v AND sizeof($v) AND is_array($v));
}

function fnNumber($price)
{
	return number_format($price, 0, ' ', ' ');
}

function fnMillion($price)
{
	$price = round(($price / 1000000), 1);
	$price = str_replace('.', ',', $price);
	return $price;
}

function ksortArray(&$array)
{
	ksort($array);
	foreach ($array as $key => &$item)
	{
		if (is_array($item))
		{
			ksortArray($item);
		}
	}
}

function fn_phone_theme($phone, $format = ['7' => '###-##-##', '8' => '+# ###-##-##', '10' => '+7 (###) ###-##-##', '11' => '+# (###) ###-##-##'], $mask = '#')
{
	$phone = preg_replace('/[^0-9]/', '', $phone);
	if (strlen($phone) > 10)
	{
		$phone = preg_replace('/^8/', '7', $phone);
	}

	if (is_array($format))
	{
		if (array_key_exists(strlen($phone), $format))
			$format = $format[strlen($phone)];
		else
			return false;
	}

	$pattern = '/'.str_repeat('([0-9])?', substr_count($format, $mask)).'(.*)/';

	$format = preg_replace_callback(
		str_replace('#', $mask, '/([#])/'),
		function () use (&$counter) {
			return '${'.(++$counter).'}';
		},
		$format
	);

	return ($phone) ? trim(preg_replace($pattern, $format, $phone, 1)) : false;
}

function fn_morph($n, $f1, $f2, $f5) //Функция для получения слово для числительного (ex товаров)
{
	$n = abs(intval($n)) % 100;
	if ($n > 10 && $n < 20)	return $f5;
	$n = $n % 10;
	if ($n > 1 && $n < 5) return $f2;
	if ($n == 1) return $f1;

	return $f5;
}

function find_parent($sect){ //Найти самого старшего родителя
    $res = CIBlockSection::GetByID($sect);  
    if($ar_res = $res->GetNext())
        $parent_sec_id = $ar_res['IBLOCK_SECTION_ID'];
    if($parent_sec_id!='')		
    {
        $res2 = CIBlockSection::GetByID($parent_sec_id); 
        if($ar_res2 = $res2->GetNext())
            $parent_sec_id2 = $ar_res2['IBLOCK_SECTION_ID'];
        if($parent_sec_id2!='') 
        {return find_parent($parent_sec_id);}
        else 
        {return $parent_sec_id;}
    }
    else
    {return $sect;}
}
function is_odd($var)
{
    return $var & 1;
}
```
