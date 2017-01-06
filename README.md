#Модуль для Битрикс «GeoIp Api»

[Api](#api)

[Пример использования](#Пример-использования)

[Требования](#Требования)

[Контакты](#Контакты)

##Описание
Модуль предоставляет api для определения местоположения по ip-адресу. Если ip-адрес не указан явно, то местоположение определяется по текущему ip пользователя.

В местоположение входят:

* город;
* код страны;
* название страны на русском языке;
* регион;
* район;
* ширина и долгота;
* диапазон ip-адресов, в который входит переданный.

Модуль доступен на [Маркетплейсе Битрикса](http://marketplace.1c-bitrix.ru/solutions/rover.geoip/).

##Api
###`\Rover\GeoIp\Location`
####`public static \Rover\GeoIp\Location::getInstance($ip = null, $charset = self::CHARSET__UTF_8)`
Метод возвращает объект `\Rover\GeoIp\Location` для переднного ip-адреса. Если ip-адрес не передан, то объект возвращается для текуего ip пользователя.

Вторым параметром можно передать кодировку возвращаемых данных. Если на не передана, то по умолчанию берется utf-8.
####`public static getCurIp()`
Возвращает ip-адрес текущего пользователя.
####`public getData()`
Возвращает ассоциативный массив со всеми данными, которые удалось получить по ip. Если данные получить не удалось, в массиве возвращается только один элемент с ключем `ip`, с котором находится переданный ip.

	[
		'ip'            => 'xxx.xxx.xxx.xxx',
		'inetnum'       => '...',
		'country'       => '...',
		'city'          => '...',
		'region'        => '...',
		'district'      => '...',
		'lat'           => '...',
		'lng'           => '...'
	]	
	
####`public getCity()`
Возвращает город, либо `null`, если не удалось получить результат.	
<<<<<<< HEAD
###`public getCountry()`
Возвращает код страны, либо `null`, если не удалось получить результат.	
###`public getCountryName($lang = LANGUAGE_ID)`
Возвращает название страны для переданного кода языка (по умолчанию - текщуий язык сайта), либо `null`, если не удалось получить результат. По умолчанию в модуле доступны названия только на русском языке.
###`public getRegion()`
Возвращает регион, либо `null`, если не удалось получить результат.	
###`public getDistrict()`
Возвращает район, либо `null`, если не удалось получить результат.
###`public getLat()`
Возвращает широту, либо `null`, если не удалось получить результат.	
###`public getLng()`
Возвращает долготу, либо `null`, если не удалось получить результат.					
###`public getInetnum()`
Возвращает диапазон адресов, в скоторый входит переданный ip, либо `null`, если не удалось получить результат.	
#Пример использования
=======
####`public getCountry()`
Возвращает код страны, либо `null`, если не удалось получить результат.	
####`public getCountryName($lang = LANGUAGE_ID)`
Возвращает название страны для переданного кода языка (по умолчанию - текщуий язык сайта), либо `null`, если не удалось получить результат. По умолчанию в модуле доступны названия только на русском языке.
####`public getRegion()`
Возвращает регион, либо `null`, если не удалось получить результат.	
###`public getDistrict()`
Возвращает район, либо `null`, если не удалось получить результат.
####`public getLat()`
Возвращает широту, либо `null`, если не удалось получить результат.	
####`public getLng()`
Возвращает долготу, либо `null`, если не удалось получить результат.					
####`public getInetnum()`
Возвращает диапазон адресов, в скоторый входит переданный ip, либо `null`, если не удалось получить результат.	
##Пример использования
>>>>>>> 2aebef30ed007ea9deda691959991bdf8744c3c2

	\Bitrix\Main\Loader::includeModule('rover.geoip');

	echo \Rover\GeoIp\Location::getCurIp(); // текущий ip

	$location = \Rover\GeoIp\Location::getInstance('5.255.255.88'); // yandex.ru
	
	echo $location->getIp();        // 5.255.255.88
	echo $location->getCity();      // Москва
	echo $location->getCountry();   // RU
	echo $location->getCountryName();  // Россия
	echo $location->getRegion();    // Москва
	echo $location->getDistrict();  // Центральный федеральный округ
	echo $location->getLat();       // 55.755787
	echo $location->getLng();       // 37.617634
	echo $location->getInetnum();   // 5.255.252.0 - 5.255.255.255
	
##Требования	
Для работы «GeoIp Api» необходим установленный на хостинге php версии 5.4 или выше.
##Контакты
По всем вопросам вы можете связаться со мной по email: rover.webdev@gmail.com, либо через форму на сайте http://rover-it.me.
