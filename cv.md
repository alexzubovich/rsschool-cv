# Alexey Zubovich

## Contact information:
Phone: +375 44 542-66-51
Email: alex.zubovich@gmail.com

## About me:
For 2 years I worked as a content manager for an organization that sold mobile content. Since 2012 I have been working as an SEO specialist in an advertising agency. In addition, I have several Internet projects of my own.

### Education:
* University: Belarusian State University of Informatics and Radioelectronics
* Python course (Udemy)
* SEO course (P. Aleksandrov)
* SEO course (D. Shahov)

### Skills:
* HTML + CSS (middle)
* JS (basic)
* Python (basic)
* SEO (high)

### Languages:
* Belorusian - Native
* Russian - Native
* English: A1

## Code example:
Creating a text analyzer (snippet).

```php
if (isset($_POST['submit_base_form'])) {
	$words_list = explode("\r\n", $_POST[textarea_words]);
	$sites_list = explode("\r\n", $_POST[textarea_sites]);

	for ($i=0; $i<count($words_list); $i++) {$words_base_list[] = $_POST[$i];}

		echo "<table style='border:1px solid;'><tr><th rowspan='2'></th>";
		foreach ($words_list as $value) {echo "<th colspan='4'>".$value."</th>";}
		echo "<th rowspan='2'>Words</th><th rowspan='2'>Symbols</th></tr>";
		
		echo "<tr>";
		foreach ($words_list as $value) {echo "<td>Common</td><td>Common %</td><td>Exect</td><td>Exect %</td>";} echo "</tr>";

	foreach ($sites_list as $site) {
		$parse_text_funct = parse_text($site, $words_list);
		$exect_words = $parse_text_funct[2];
		/* подсчет общих слов */
		foreach ($words_base_list as $base_word) {
			$base_word_count = substr_count($parse_text_funct[3], " ".$base_word." "); 
			$base_word_count_array[] = $base_word_count;
		}

			echo "<tr><td>".$site."</td>"; for($i=0;$i<count($words_list);$i++) {
			echo "<td>".$base_word_count_array[$i]."</td><td>".number_format($base_word_count_array[$i]*100/$parse_text_funct[0], 2, ',', '')."</td><td>".$exect_words[$i]."</td><td>".number_format($exect_words[$i]*100/$parse_text_funct[0], 2, ',', '')."</td>";
			}
			echo "<td>".$parse_text_funct[0]."</td><td>".$parse_text_funct[1]."</td>";
		$base_word_count_array = array();
		
	}

		echo "</tr></table>";
		$base_word_count_array = array();

}
```