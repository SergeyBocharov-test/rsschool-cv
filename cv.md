# Curriculum Vitae

## Name

**Sergey Bocharov**

## Contact and other information

* Mobile: **+7-906-710-46-60**
* Email: <work.sergey.bocharov@ya.ru>
* Discord: *Djeeshka#6034*
* Address: Moscow, Russia
* Date of birth: 30/.09/.1992

## About myself

I am a humble man looking for my place in life and a pleasant activity to earn money.
I don't like to lie and assure that I'm great in quickly learning, but I have a desire and goals.
I hope to accomplish this course and learn new things.
Other people tend to describe my personal qualities as dependable, versatile, kind and friendly.

## Skills

* _Surface level knowladge of HTML, CSS, PHP, MySQL, Git_
* Variety of graphical software:
   * _Proficent in **Adobe Photoshop**_
   * _Advanced in **Adobe Flash** and(or) **Adobe Animate**_
   * _Intermediate in **Adobe Illustrator**, **Adobe InDesign** and **Krita**_
   * _Beginner in **Blender** and **VEGAS**_
* _Basic knowladge of administration and virtualisation software for Windows and Linux (Gentoo) OS_
	
## Code example

* Sentence generator (PHP)

A little _somewhat simple_ PHP sentence generator for a Twitch chat bot.
It aims to create a sentence of execution of an action from user to another random user from the same chat for fun.
There are also options to exclude certain users from being choosed by random and options for different outcome _chance_.

Some values are edited out ( `------` ), in order to shorten the example and not expose anything valuable.

It can be seen in action [HERE](https://www.djee.ml/lj_poke.php?user=Uzver&channel=lady_jill).
<details> <summary>CODE</summary>
<pre><code class="language-php">
<?php
if(isset($_GET['channel'])) {

	/* Скрипт на рандомного юзера из чата канала */
	
	$channel = $_GET['channel'];
	
	if($channel != '------') {
	echo 'Хух, откуда у вас этот скрипт? Если хотите им воспользоваться - обратитесь к ------';
	} else {
	
	$try = 1;	// счетчик попыток
	
	Start:

	$cont_chatters = json_decode(file_get_contents('http://tmi.twitch.tv/group/user/'.$channel.'/chatters'), true);	// Получение списка пользователей в чате.	
	$chatters = array_merge($cont_chatters['chatters']['moderators'], $cont_chatters['chatters']['viewers']);		// Фильтруем и объединяем нужные группы пользователей.
	$rnd_chatter = $chatters[mt_rand(0, count($chatters) - 1)];														// Берём случайного пользователя.
	//	Так как с IRC сервера берутся имена пользователей без учета регистра - преобразуем полученное имя пользователя в его настоящее с учетом регистра.
	
	$cont_display_name = json_decode(file_get_contents('https://api.twitch.tv/v5/users?login='.$rnd_chatter.'&client_id=------'), true);	// Получение данных о пользователе от Твичевского Кракена.       	
	$rnd_user = $cont_display_name["users"][0]["display_name"]; // Получаем имя пользователя с учетом регистра символов.

	if(isset($_GET['user'])) {	// получаем параметр от бота.

	$user = $_GET['user'];		// получаем параметр от бота.
	
	if(isset($rnd_user)) {
		$rnd1 = mt_rand(0, 3); // Random Number 0-3
		$rnd2 = mt_rand(0, 3); // Random Number 0-3
	
		// CREATURES
		$creature1[0] = //cute
		[
			'кролика ?? , который тычет носом в ',
			'------'
		];
		$creature1[1] = //not cute
		[
			'гоблина, который',
			'------'
		];
		// ITEMS
		$item1[0] = //good
		[
			' пускает луч добра в ',
			'------'
		];
		$item1[1] = //normal
		[
			' тычет в ',
			'------'
		];
		$item1[2] = //strange
		[
			' метает гуся в ',
			'------'
		];
		$item1[3] = //bad
		[
			' пускает лучи хаоса в ',
			'------'
		];	
		// TARGETS
		// SELF
		$self[0] = ' своё '; // средний род
		//
		$target1[0] = [ // средний род
			'лицо',
			'------'
		];
		// SELF
		$self[1] = ' свой '; // мужской род
		//
		$target1[1] = [ // мужской род
			'глаз ?? ',
			'------'
		];
		// SELF
		$self[2] = ' свою '; // женский род
		//
		$target1[2] = [ // женский род
			'ноздрю',
			'------'
		];
		// SELF
		$self[3] = ' свои '; // множественное число	
		//
		$target1[3] = [ // множественное число
			'зубы',
			'------'
		];	
		// ENDINGS	
		$endinspecial2[0] = [ // good
			'. Отлично!',
			'------'
		];
		$endinspecial2[1] = [ // normal
			'. Произвол!',
			'------'
		];
		$endinspecial2[2] = [ // strange
			'. Как необычно.',
			'------'
		];
		$endinspecial2[3] = [ // bad
			'. Какая жестокость!',
			'------',
		];
		$ending_self = [ // self
			'. Вот это меткость.',
			'------'
		];
		$ending_special1 = [
			'но передумывает. Молодец.',
			'------'
		];
		$ending_special2 = [
			'но тот на кухне. Как жалко',
			'------'
		];
			
		switch ($rnd_user) {
		
			case $user: // SELF
				echo $user.$item1[$rnd1][mt_rand(0, count($item1[$rnd1]) - 1)].$self[$rnd2].$target1[$rnd2][mt_rand(0, count($target1[$rnd2]) - 1)].$ending_self[mt_rand(0, count($ending_self) - 1)];
				break;		
			case '------': // случай на конкретные имя юзера.
				if ($rnd1 == 0){ // 1/4
						echo $user.$item1[0][mt_rand(0, count($item1[0]) - 1)].$target1[$rnd2][mt_rand(0, count($target1[$rnd2]) - 1)].' ------'.$endinspecial2[0][mt_rand(0, count($endinspecial2[0]) - 1)];
					} else {
						echo $user.' собирается что-то сделать с ------, '.$ending_special1[mt_rand(0, count($ending_special1) - 1)];
					}
				break;
				
			case '------': // случай на конкретные имя юзера.
				if (mt_rand(0, 29) == 23) { // 1/30
						echo $user.' собирается что-то сделать с ------, '.$ending_special2[mt_rand(0, count($ending_special2) - 1)];
					} else {
						echo $user.$item1[$rnd1][mt_rand(0, count($item1[$rnd1]) - 1)].$target1[$rnd2][mt_rand(0, count($target1[$rnd2]) - 1)].' '.$rnd_user.$endinspecial2[$rnd1][mt_rand(0, count($endinspecial2[$rnd1]) - 1)];				
					}
				break;
				
			default: // используетяс как особый редкий случай.
					if(mt_rand(0, 99) == 8) {
							echo '------ '.$user.' ------ '.$rnd_user.', ------. '.$rnd_user.' ------ '.$rnd_user.' ------!';
						} elseif (mt_rand(0, 99) == 13){
							echo 'Ни с того ни с сего '.$rnd_user.', предвидя неловкую ситуацию, останавливает '.$user.'. Любопытно.';
						} else {
							echo $user.$item1[$rnd1][mt_rand(0, count($item1[$rnd1]) - 1)].$target1[$rnd2][mt_rand(0, count($target1[$rnd2]) - 1)].' '.$rnd_user.$endinspecial2[$rnd1][mt_rand(0, count($endinspecial2[$rnd1]) - 1)];
						}
				break;
			}
			
			} else if ($try > 1){ // в случае если что-то пошло не так и произошла повторная попытка.
				
				$error_rnd_user = [
					'А если бы я вас тыкал, вам было бы приятно? А если бы прунькнул? М? Ну ладно, попробуйте ещё раз. Kappa',
					'------'
				];
				
				echo $error_rnd_user[mt_rand(0, count($error_rnd_user) - 1)];
				
				} else {	// если что-то пошло не так - попробовать снова.
					$try += 1;
					sleep(0.01);
					goto Start;				
				}
			
	} else {
		echo "Ошибка: Не задан user.";
		}
	
	}
	
	} else {
		echo "Ошибка: Не задан channel.";
		}
?></code></pre></details>
## Work experience

* **2017-present**; **Freelance graphic designer**
	* Various unofficial freelance work and comissions related to graphical design.

* ООО «Рекламное агентство «Про Медиа» _(Advertising Agency)_; **2014-2017**; Moscow, Russia; **Designer**	
	* Development and creation of various advertisement materials. Primarily flash/html5 web banners for various of advertisement platforms.

* ООО «Белый Ветер ЦИФРОВОЙ» _(Retail electronics stores)_; **2013**; Moscow, Russia; **Junior sales assistant**	
	* Consulting customers about various hardware.
		
## Education
* General school education
	
* «Московский государственный университет дизайна и технологии» _(Moscow State University of Design and Technology)_; **2011-2013**; Moscow, Russia		
	* Faculty: МиИТ _(Mechatronics and Information Technologies)_		
	* Specialty: «Информационные системы и технологии» _(Information systems and technologies)_	
	* **Unfinished**	

* «Московский технический университет связи и информатики» _(Moscow Technical University of Communications and Informatics)_; **2010**; Moscow, Russia		
	* Faculty: ИТ _(Information Technologies)_
	* **Unfinished**

* «Столичный институт экономики и финансов» _(Capital Institute of Economics and Finance)_; **2020**; Moscow, Russia	
	* Training course: «Администрирование ОС Windows Server и ОС Linux» _(Administration of Windows Server and Linux OS)_	
	* Qualification: «Администратор компьютерных сетей на основе операциооных систем Windows Server и Unix (Linux)» _(Administrator of computer networks based on Windows Server and Unix (Linux) operating systems))_

## English skills
* Level: **A2**
	
Personally I was never tested on that topic and I feel like it might be actually B2, but I'm not very confident.
I can read and listen well, but struggle to confidently speak.
That's my reasoning behind choosing "A2" instead of anything else.
