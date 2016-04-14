#Automatic word creation script

# SQL query to create words automatically #

drop table terms;
drop table inflections;
create table inflections (wordend varchar(100), primary key(wordend));
create table terms (original varchar(100), primary key(original));

INSERT INTO `inflections` (`wordend` ) VALUES ('ने'), ('नी'), ('स'), ('शी'), ('ला'), ('त'), ('ना'), ('ऊन'), ('हून'), ('ई'), ('नो'), ('हो'), ('मुळे'), ('बरोबर'), ('लगत'), ('द्वारे'), ('कडून'), ('प्रमाणे'), ('सारखा'), ('साठी'), ('करिता'), ('कडे'), ('ऐवजी'), ('अर्थी'), ('पेक्षा'), ('पासून'), ('वाचून'), ('खेरीज'), ('शिवाय'), ('नंतर'), ('विषयी'), ('संबंधी'), ('चा'), ('ची'), ('चे'), ('च्या'), ('मध्ये'), ('खाली'), ('पलीकडे'), ('पैकी'), ('बाहेर'), ('समोर'), ('भोवती');

INSERT INTO `terms` (`original` ) VALUES ('अंगा'), ('साहित्या');

SELECT concat( original, wordend ) AS neword FROM `terms` INNER JOIN inflections ORDER BY neword;

# The following words are generated when the above query is run. #

अंगाअर्थी अंगाई अंगाऊन अंगाऐवजी अंगाकडून अंगाकडे अंगाकरिता अंगाखाली अंगाखेरीज अंगाचा अंगाची अंगाचे अंगाच्या अंगात अंगाद्वारे अंगानंतर अंगाना अंगानी अंगाने अंगानो अंगापलीकडे अंगापासून अंगापेक्षा अंगापैकी अंगाप्रमाणे अंगाबरोबर अंगाबाहेर अंगाभोवती अंगामध्ये अंगामुळे अंगालगत अंगाला अंगावाचून अंगाविषयी अंगाशिवाय अंगाशी अंगास अंगासंबंधी अंगासमोर अंगासाठी अंगासारखा अंगाहून अंगाहो

साहित्याअर्थी साहित्याई साहित्याऊन साहित्याऐवजी साहित्याकडून साहित्याकडे साहित्याकरिता साहित्याखाली  साहित्याखेरीज साहित्याचा साहित्याची साहित्याचे साहित्याच्या साहित्यात साहित्याद्वारे साहित्यानंतर साहित्याना साहित्यानी साहित्याने साहित्यानो साहित्यापलीकडे साहित्यापासून साहित्यापेक्षा साहित्यापैकी साहित्याप्रमाणे साहित्याबरोबर साहित्याबाहेर साहित्याभोवती साहित्यामध्ये साहित्यामुळे साहित्यालगत साहित्याला साहित्यावाचून साहित्याविषयी साहित्याशिवाय साहित्याशी साहित्यास साहित्यासंबंधी साहित्यासमोर साहित्यासाठी साहित्यासारखा साहित्याहून साहित्याहो


# Conclusion: #

The automatic word creation technique works for the simple words like "अंगा" but it does not work for words like "साहित्या"

Wrong words: साहित्याई साहित्याऊन

never used words: साहित्यानो साहित्याहो

rarely used words: साहित्याअर्थी साहित्याना साहित्यानी साहित्यालगत

The word "साहित्या" created 43 words and out of it 8 words mentioned above are not worth accepting in the spell check database. In other words 20% of the words generated needs to be scrapped and therefore this solution is not acceptable.