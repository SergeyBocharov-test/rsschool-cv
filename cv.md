# Curriculum Vitae

## 1. Name

    **Sergey Bocharov**
	
## 2. Contact and other information

	* Mobile: **+7-906-710-46-60**
	* Email: <work.sergey.bocharov@ya.ru>
	* Discord: *Djeeshka#6034*
    * Address: Moscow, Russia
	* Date of birth: 30/.09/.1992

## 3. About myself

    I am a humble man looking for my place in life and a pleasant activity to earn money.
	I don't like to lie and assure that I'm great in quickly learning, but I have a desire and goals.
	I hope to accomplish this course and learn new things.
	Other people tend to describe my personal qualities as dependable, versatile, kind and friendly.

## 4. Skills

    _Surface level knowladge of HTML, CSS, PHP, MySQL, Git_
	
    * Variety of graphical software:
        _Proficent in **Adobe Photoshop**_
        _Advanced in **Adobe Flash** and(or) **Adobe Animate**_
        _Intermediate in **Adobe Illustrator**, **Adobe InDesign** and **Krita**_
        _Beginner in **Blender** and **VEGAS**_
		
	_Basic knowladge of administration and virtualisation software for Windows and Linux (Gentoo) OS_
	
## 5. Code examples

    * Sentence generator (PHP)
        A little _somewhat simple_ PHP sentence generator for a Twitch chat bot.
	
	    It aims to create a sentence of execution of an action from user to another random user from the same chat for fun.
		There are also options to exclude certain users from being choosed by random and options for different outcome _chance_.
		
		Some values are edited out (`------`), in order to shorten the example and not expose anything valuable.
		
		It can be seen in action [HERE](https://www.djee.ml/lj_poke.php?user=Uzver&channel=lady_jill).
	
        ```php
        <?php
        if(isset($_GET['channel'])) {
        
        	/* ������ �� ���������� ����� �� ���� ������ */
        	
        	$channel = $_GET['channel'];
        	
        	if($channel != '------') {
        	echo '���, ������ � ��� ���� ������? ���� ������ �� ��������������� - ���������� � ------';
        	} else {
        	
        	$try = 1;	// ������� �������
        	
        	Start:
        
        	$cont_chatters = json_decode(file_get_contents('http://tmi.twitch.tv/group/user/'.$channel.'/chatters'), true);	// ��������� ������ ������������� � ����.	
        	$chatters = array_merge($cont_chatters['chatters']['moderators'], $cont_chatters['chatters']['viewers']);		// ��������� � ���������� ������ ������ �������������.
        	$rnd_chatter = $chatters[mt_rand(0, count($chatters) - 1)];														// ���� ���������� ������������.
        	
        //	��� ��� � IRC ������� ������� ����� ������������� ��� ����� �������� - ����������� ���������� ��� ������������ � ��� ��������� � ������ ��������.
        	
        	$cont_display_name = json_decode(file_get_contents('https://api.twitch.tv/v5/users?login='.$rnd_chatter.'&client_id=------'), true);	// ��������� ������ � ������������ �� ����������� �������.       	
        	$rnd_user = $cont_display_name["users"][0]["display_name"]; // �������� ��� ������������ � ������ �������� ��������.
        
        	if(isset($_GET['user'])) {	// �������� �������� �� ����.
        
        	$user = $_GET['user'];		// �������� �������� �� ����.
        	
        	if(isset($rnd_user)) {
        		$rnd1 = mt_rand(0, 3); // Random Number 0-3
        		$rnd2 = mt_rand(0, 3); // Random Number 0-3
        	
        		// CREATURES
        		$creature1[0] = //cute
        		[
        			'������� ?? , ������� ����� ����� � ',
        			'------'
        		];
        		$creature1[1] = //not cute
        		[
        			'�������, �������',
        			'------'
        		];
        		// ITEMS
        		$item1[0] = //good
        		[
        			' ������� ��� ����� � ',
        			'------'
        		];
        		$item1[1] = //normal
        		[
        			' ����� � ',
        			'------'
        		];
        		$item1[2] = //strange
        		[
        			' ������ ���� � ',
        			'------'
        		];
        		$item1[3] = //bad
        		[
        			' ������� ���� ����� � ',
        			'------'
        		];	
        		// TARGETS
        		// SELF
        		$self[0] = ' ��� '; // ������� ���
        		//
        		$target1[0] = [ // ������� ���
        			'����',
        			'------'
        		];
        		// SELF
        		$self[1] = ' ���� '; // ������� ���
        		//
        		$target1[1] = [ // ������� ���
        			'���� ?? ',
        			'------'
        		];
        		// SELF
        		$self[2] = ' ���� '; // ������� ���
        		//
        		$target1[2] = [ // ������� ���
        			'������',
        			'------'
        		];
        		// SELF
        		$self[3] = ' ���� '; // ������������� �����	
        		//
        		$target1[3] = [ // ������������� �����
        			'����',
        			'------'
        		];	
        		// ENDINGS	
        		$endinspecial2[0] = [ // good
        			'. �������!',
        			'------'
        		];
        		$endinspecial2[1] = [ // normal
        			'. ��������!',
        			'------'
        		];
        		$endinspecial2[2] = [ // strange
        			'. ��� ��������.',
        			'------'
        		];
        		$endinspecial2[3] = [ // bad
        			'. ����� ����������!',
        			'------',
        		];
        		$ending_self = [ // self
        			'. ��� ��� ��������.',
        			'------'
        		];
        		$ending_special1 = [
        			'�� ������������. �������.',
        			'------'
        		];
        		$ending_special2 = [
        			'�� ��� �� �����. ��� �����',
        			'------'
        		];
        			
        		switch ($rnd_user) {
        		
        			case $user: // SELF
        				echo $user.$item1[$rnd1][mt_rand(0, count($item1[$rnd1]) - 1)].$self[$rnd2].$target1[$rnd2][mt_rand(0, count($target1[$rnd2]) - 1)].$ending_self[mt_rand(0, count($ending_self) - 1)];
        				break;		
        			case '------': // ������ �� ���������� ��� �����.
        				if ($rnd1 == 0){ // 1/4
        						echo $user.$item1[0][mt_rand(0, count($item1[0]) - 1)].$target1[$rnd2][mt_rand(0, count($target1[$rnd2]) - 1)].' ------'.$endinspecial2[0][mt_rand(0, count($endinspecial2[0]) - 1)];
        					} else {
        						echo $user.' ���������� ���-�� ������� � ------, '.$ending_special1[mt_rand(0, count($ending_special1) - 1)];
        					}
        				break;
        				
        			case '------': // ������ �� ���������� ��� �����.
        				if (mt_rand(0, 29) == 23) { // 1/30
        						echo $user.' ���������� ���-�� ������� � ------, '.$ending_special2[mt_rand(0, count($ending_special2) - 1)];
        					} else {
        						echo $user.$item1[$rnd1][mt_rand(0, count($item1[$rnd1]) - 1)].$target1[$rnd2][mt_rand(0, count($target1[$rnd2]) - 1)].' '.$rnd_user.$endinspecial2[$rnd1][mt_rand(0, count($endinspecial2[$rnd1]) - 1)];				
        					}
        				break;
        				
        			default: // ������������ ��� ������ ������ ������.
        					if(mt_rand(0, 99) == 8) {
        							echo '------ '.$user.' ------ '.$rnd_user.', ------. '.$rnd_user.' ------ '.$rnd_user.' ------!';
        						} elseif (mt_rand(0, 99) == 13){
        							echo '�� � ���� �� � ���� '.$rnd_user.', �������� �������� ��������, ������������� '.$user.'. ���������.';
        						} else {
        							echo $user.$item1[$rnd1][mt_rand(0, count($item1[$rnd1]) - 1)].$target1[$rnd2][mt_rand(0, count($target1[$rnd2]) - 1)].' '.$rnd_user.$endinspecial2[$rnd1][mt_rand(0, count($endinspecial2[$rnd1]) - 1)];
        						}
        				break;
        			}
        			
        			} else if ($try > 1){ // � ������ ���� ���-�� ����� �� ��� � ��������� ��������� �������.
        				
        				$error_rnd_user = [
        					'� ���� �� � ��� �����, ��� ���� �� �������? � ���� �� ���������? �? �� �����, ���������� ��� ���. Kappa',
        					'------'
        				];
        				
        				echo $error_rnd_user[mt_rand(0, count($error_rnd_user) - 1)];
        				
        				} else {	// ���� ���-�� ����� �� ��� - ����������� �����.
        					$try += 1;
        					sleep(0.01);
        					goto Start;				
        				}
        			
        	} else {
        		echo "������: �� ����� user.";
        		}
        	
        	}
        	
        	} else {
        		echo "������: �� ����� channel.";
        		}
        
        ?>
        ```
## 6. Work experience

	* **2017-present**; **Freelance graphic designer**
		* Various unofficial freelance work and comissions related to graphical design.

    * ��� ���������� ��������� ���� ����� _(Advertising Agency)_; **2014-2017**; Moscow, Russia; **Designer**
		* Development and creation of various advertisement materials. Primarily flash/html5 web banners for various of advertisement platforms.
	
	* ��� ������ ����� �������ɻ _(Retail electronics stores)_; **2013**; Moscow, Russia; **Junior sales assistant**
		* Consulting customers about various hardware.
		
## 7. Education

	* General school education
	
	* ����������� ��������������� ����������� ������� � ���������� _(Moscow State University of Design and Technology)_; **2011-2013**; Moscow, Russia
		
		* Faculty: ���� _(Mechatronics and Information Technologies)_
		
		* Specialty: ��������������� ������� � ���������� _(Information systems and technologies)_
		
		* **Unfinished**
	
	* ����������� ����������� ����������� ����� � ����������� _(Moscow Technical University of Communications and Informatics)_; **2010**; Moscow, Russia
		
		* Faculty: �� _(Information Technologies)_
		
		* **Unfinished**
		
	* ���������� �������� ��������� � �������� _(Capital Institute of Economics and Finance)_; **2020**; Moscow, Russia
	
		* Training course: ������������������ �� Windows Server � �� Linux� _(Administration of Windows Server and Linux OS)_
		
		* Qualification: �������������� ������������ ����� �� ������ ������������ ������ Windows Server � Unix (Linux)� _(Administrator of computer networks based on Windows Server and Unix (Linux) operating systems))_

## 8. English skills
	
	* Level: **A2**
	
		Personally I was never tested on that topic and I feel like it might be actually B2, but I'm not very confident.
		I can read and listen well, but struggle to confidently speak.
		That's my reasoning behind choosing "A2" instead of anything else.

