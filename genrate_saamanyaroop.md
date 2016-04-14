Here is an example of how many words can be generated from a single word "घोडा". The single and plural form is not included in the following table ('घोडा', 'घोडे')

एकवचनाच्या सामान्यरूपात "घोड्यांला", "घोड्यांने" व "घोड्यानो" अशी चुकीची रुपे बनतात तर अनेकवचनात "घोड्याना", "घोड्यानी" अशी चुकीची रुपे दिसतात. शेवटच्या क्वेरीमध्ये हे ५ शब्द गाळले आहेत.

### घोडा शब्दाची सामान्यरूपे ###

drop table if exists samanyaroop;

CREATE TABLE samanyaroop (word varchar(50) NOT NULL, PRIMARY KEY  (word)) ENGINE=MyISAM DEFAULT CHARSET=utf8;


INSERT INTO samanyaroop VALUES
('घोड्या'), ('घोड्याअंती'), ('घोड्याअर्थी'), ('घोड्याअलीकडे'), ('घोड्याआत'), ('घोड्याआता'), ('घोड्याआतून'), ('घोड्याआधी'), ('घोड्याउलट'), ('घोड्याउलटे'), ('घोड्याऐवजी'), ('घोड्याकडून'), ('घोड्याकडे'), ('घोड्याकरवी'), ('घोड्याकरिता'), ('घोड्याकरून'), ('घोड्याकारणे'), ('घोड्याकेवळ'), ('घोड्याखाली'), ('घोड्याखालून'), ('घोड्याखेरीज'), ('घोड्याच'), ('घोड्याचा'), ('घोड्याची'), ('घोड्याच्या'), ('घोड्याचे'), ('घोड्याजवळ'), ('घोड्याजागी'), ('घोड्याजोगा'), ('घोड्याठायी'), ('घोड्यात'), ('घोड्यातम'), ('घोड्यातर'), ('घोड्याते'), ('घोड्यादेखील'), ('घोड्याद्वारा'), ('घोड्यानंतर'), ('घोड्यानजीक'), ('घोड्याना'), ('घोड्यानिमित्त'), ('घोड्यानिशी'), ('घोड्यानिहाय'), ('घोड्यानी'), ('घोड्यानो'), ('घोड्यापक्षी'), ('घोड्यापण'), ('घोड्यापरता'), ('घोड्यापरीस'), ('घोड्यापर्यंत'), ('घोड्यापावेतो'), ('घोड्यापाशी'), ('घोड्यापासून'), ('घोड्यापुढून'), ('घोड्यापुढे'), ('घोड्यापूर्वी'), ('घोड्यापेक्षा'), ('घोड्यापैकी'), ('घोड्यापोटी'), ('घोड्याप्रत'), ('घोड्याप्रति'), ('घोड्याप्रमाणे'), ('घोड्याप्रित्यर्थ'), ('घोड्याफक्त'), ('घोड्याबदली'), ('घोड्याबद्दल'), ('घोड्याबरहुकूम'), ('घोड्याबरीक'), ('घोड्याबरोबर'), ('घोड्याबाहेर'), ('घोड्याबी'), ('घोड्याभर'), ('घोड्याभोवती'), ('घोड्यामधून'), ('घोड्यामध्ये'), ('घोड्यामागाहून'), ('घोड्यामागून'), ('घोड्यामागे'), ('घोड्यामाजी'), ('घोड्यामात्र'), ('घोड्यामुळे'), ('घोड्याम्हणून'), ('घोड्यायोगे'), ('घोड्यायोग्य'), ('घोड्यालागी'), ('घोड्यावतीने'), ('घोड्यावरी'), ('घोड्यावरील'), ('घोड्यावरून'), ('घोड्यावाचून'), ('घोड्याविना'), ('घोड्याविरुद्ध'), ('घोड्याविशी'), ('घोड्याविषयी'), ('घोड्यावीण'), ('घोड्याव्यतिरिक्त'), ('घोड्याशिवाय'), ('घोड्याशी'), ('घोड्याशेजारी'), ('घोड्यास'), ('घोड्यासंगती'), ('घोड्यासंगे'), ('घोड्यासंबंधी'), ('घोड्यासकट'), ('घोड्यासम'), ('घोड्यासमवेत'), ('घोड्यासमान'), ('घोड्यासमीप'), ('घोड्यासमोर'), ('घोड्यासवे'), ('घोड्यासह'), ('घोड्यासहित'), ('घोड्यासाठी'), ('घोड्यासारखा'), ('घोड्यासुद्धा'), ('घोड्यास्तव'), ('घोड्याही'), ('घोड्याहून'), ('घोड्याला'), ('घोड्याने')  ;



(select 'घोडा' as singular, '' as pratya, 'घोडे' as plural) union (SELECT if( (word = 'घोड्यांला' OR word = 'घोड्यांने' OR word = 'घोड्यानो' OR word = 'घोड्याना' OR word = 'घोड्यानी'), '', word ) AS singular, replace( word, 'घोड्या', '' ) AS pratya, if( ( replace( word, 'घोड्या', 'घोड्यां' ) = 'घोड्यांला' OR replace( word, 'घोड्या', 'घोड्यां' ) = 'घोड्यांने' OR replace( word, 'घोड्या', 'घोड्यां' ) = 'घोड्यानो' OR replace( word, 'घोड्या', 'घोड्यां' ) = 'घोड्याना' OR replace( word, 'घोड्या', 'घोड्यां' ) = 'घोड्यानी' OR replace( word, 'घोड्या', 'घोड्यां' ) = 'घोड्यां' ) , '', replace( word, 'घोड्या', 'घोड्यां' ) ) AS plural FROM samanyaroop
order by pratya in ('स', 'ला', 'ने', 'शी', 'हून', 'चा', 'ची', 'चे', 'च्या', 'त', 'ना', 'नी', 'नो'), word
)