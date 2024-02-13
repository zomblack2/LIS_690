# grep

Using scopus.bib file on virtual machine

## Basic Commands

    grep "Irish Dance" scopus.bib
        title = {Characteristics of Eight Irish Dance Landings Considerations for Training and Overuse Injury Prevention},
        title = {Dietary Intake, Body Composition, and Nutrition Knowledge of Irish Dancers},
        title = {‘Take Her Out and Air Her’: Irish Dances as Arranged by Stanford and Grainger},
        journal = {Complete Irish Dancer: Optimization of Health and Performance in Irish Dancers},
        title = {PERFORMED IDENTITY: A Case Study in Irish Dance},

- looks specifically for any strings that match the string in quotations
  

      grep -i "irish dance" scopus.bib
        title = {Characteristics of Eight Irish Dance Landings Considerations for Training and Overuse Injury Prevention},
        title = {The time-continuous association between turnout and axial joint moments in the competitive Irish dance ‘fly’ landing},
        title = {Dietary Intake, Body Composition, and Nutrition Knowledge of Irish Dancers},
        title = {Dance exposure, general health, sleep and injury in elite adolescent Irish dancers: A prospective study},
        title = {‘Take Her Out and Air Her’: Irish Dances as Arranged by Stanford and Grainger},
        title = {Dancing enriched whiteness: race and gender in commercial Irish dance performance from Riverdance to the Trump Inaugural Ball},
        title = {Complete Irish dancer: Optimization of health and performance in Irish dancers},
        journal = {Complete Irish Dancer: Optimization of Health and Performance in Irish Dancers},
        title = {PERFORMED IDENTITY: A Case Study in Irish Dance},
  
- ignores case with -i
  

      grep -vi "irish dance" scopus.bib
      Scopus
      EXPORT DATE: 12 February 2024

      @ARTICLE{Póvoa2023,
        author = {Póvoa, Ana Rita and Costa, Cláudia Maria and Simões, Sérgio and Azevedo, Ana Morais and Oliveira, Raul},
        title = {Irish Dancing Injuries and Associated Risk Factors: A Systematic Review},
        year = {2023},
        journal = {International Journal of Environmental Research and Public Health},
        volume = {20},
        number = {12},
        doi = {10.3390/ijerph20126190},
        url = {https://www.scopus.com/inward/record.uri?eid=2-s2.0-85163774908&doi=10.3390%2fijerph20126190&partnerID=40&md5=4ee9710222a8a756610737412a3cf0eb},
        affiliations = {Egas Moniz School of Health and Science, Almada, 2829-511, Portugal; Hospital Garcia de Orta, Almada, 2805-267, Portugal; CiiEM—Centro de Investigação Interdisciplinar Egas Moniz, Caparica, 2829-          511, Portugal; La Trobe Sport and Exercise Medicine Research Centre, La Trobe University, Melbourne, 3086, Australia; The Australian Ballet, Melbourne, 3006, Australia; Interdisciplinary Centre for the Study of           Human Performance, Neuromuscular Research Lab, Human Kinetics Faculty, University of Lisbon, Cruz Quebrada-Dafundo, 1499-002, Portugal},
        correspondence_address = {A.R. Póvoa; Egas Moniz School of Health and Science, Almada, 2829-511, Portugal; email: rpovoa@egasmoniz.edu.pt},
        publisher = {Multidisciplinary Digital Publishing Institute (MDPI)},
        issn = {16617827},
        pmid = {37372775},
        language = {English},
        abbrev_source_title = {Int. J. Environ. Res. Public Health},
        type = {Review},
        publication_stage = {Final},
        source = {Scopus},
        note = {Cited by: 0; All Open Access, Gold Open Access, Green Open Access}
        } etc.
  
- ignores case with -i and searches for anything that does not match the string with -v
  
  
      grep -vi "^irish dance" scopus.bib
          Scopus
          EXPORT DATE: 12 February 2024
          
          @ARTICLE{Póvoa2023,
                  author = {Póvoa, Ana Rita and Costa, Cláudia Maria and Simões, Sérgio and Azevedo, Ana Morais and Oliveira, Raul},
                  title = {Irish Dancing Injuries and Associated Risk Factors: A Systematic Review},
                  year = {2023},
                  journal = {International Journal of Environmental Research and Public Health},
                  volume = {20},
                  number = {12},
                  doi = {10.3390/ijerph20126190},
                  url = {https://www.scopus.com/inward/record.uri?eid=2-s2.0-85163774908&doi=10.3390%2fijerph20126190&partnerID=40&md5=4ee9710222a8a756610737412a3cf0eb},
                  affiliations = {Egas Moniz School of Health and Science, Almada, 2829-511, Portugal; Hospital Garcia de Orta, Almada, 2805-267, Portugal; CiiEM—Centro de Investigação Interdisciplinar Egas Moniz, Caparica, 2829-511, Portugal; La Trobe Sport and Exercise Medicine Research Centre, La Trobe University, Melbourne, 3086, Australia; The Australian Ballet, Melbourne, 3006, Australia; Interdisciplinary Centre for the Study of Human Performance, Neuromuscular Research Lab, Human Kinetics Faculty, University of Lisbon, Cruz Quebrada-Dafundo, 1499-002, Portugal},
                  correspondence_address = {A.R. Póvoa; Egas Moniz School of Health and Science, Almada, 2829-511, Portugal; email: rpovoa@egasmoniz.edu.pt},
                  publisher = {Multidisciplinary Digital Publishing Institute (MDPI)},
                  issn = {16617827},
                  pmid = {37372775},
                  language = {English},
                  abbrev_source_title = {Int. J. Environ. Res. Public Health},
                  type = {Review},
                  publication_stage = {Final},
                  source = {Scopus},
                  note = {Cited by: 0; All Open Access, Gold Open Access, Green Open Access}
          } etc.
  
- ignores case with -i and searches for all lines that do not match "irish dance" at the beginning of the line because of the ^
  

      grep -vi "irish$" scopus.bib
          @ARTICLE{Póvoa2023,
                  author = {Póvoa, Ana Rita and Costa, Cláudia Maria and Simões, Sérgio and Azevedo, Ana Morais and Oliveira, Raul},
                  title = {Irish Dancing Injuries and Associated Risk Factors: A Systematic Review},
                  year = {2023},
                  journal = {International Journal of Environmental Research and Public Health},
                  volume = {20},
                  number = {12},
                  doi = {10.3390/ijerph20126190},
                  url = {https://www.scopus.com/inward/record.uri?eid=2-s2.0-85163774908&doi=10.3390%2fijerph20126190&partnerID=40&md5=4ee9710222a8a756610737412a3cf0eb},
                  affiliations = {Egas Moniz School of Health and Science, Almada, 2829-511, Portugal; Hospital Garcia de Orta, Almada, 2805-267, Portugal; CiiEM—Centro de Investigação Interdisciplinar Egas Moniz, Caparica, 2829-511, Portugal; La Trobe Sport and Exercise Medicine Research Centre, La Trobe University, Melbourne, 3086, Australia; The Australian Ballet, Melbourne, 3006, Australia; Interdisciplinary Centre for the Study of Human Performance, Neuromuscular Research Lab, Human Kinetics Faculty, University of Lisbon, Cruz Quebrada-Dafundo, 1499-002, Portugal},
                  correspondence_address = {A.R. Póvoa; Egas Moniz School of Health and Science, Almada, 2829-511, Portugal; email: rpovoa@egasmoniz.edu.pt},
                  publisher = {Multidisciplinary Digital Publishing Institute (MDPI)},
                  issn = {16617827},
                  pmid = {37372775},
                  language = {English},
                  abbrev_source_title = {Int. J. Environ. Res. Public Health},
                  type = {Review},
                  publication_stage = {Final},
                  source = {Scopus},
                  note = {Cited by: 0; All Open Access, Gold Open Access, Green Open Access}
          } etc.
  
- ignores case with -i and searches for all lines that do not match "irish" at the end of the line because of the $
  

      grep -vic "irish$" scopus.bib
          418
  
- counts the number of matching lines excluding the header
  
  
      grep -Ei "(dance|music)" scopus.bib
          title = {Characteristics of Eight Irish Dance Landings Considerations for Training and Overuse Injury Prevention},
          journal = {Journal of Dance Medicine and Science},
          abbrev_source_title = {J Dance Med Sci},
          title = {The time-continuous association between turnout and axial joint moments in the competitive Irish dance ‘fly’ landing},
          title = {Dietary Intake, Body Composition, and Nutrition Knowledge of Irish Dancers},
          journal = {Journal of Dance Medicine and Science},
          affiliations = {University of Roehampton, London, United Kingdom; School of Allied Health and Health Research Institute, University of Limerick, Castletroy, Co. Limerick, Ireland; Department of Physical     
          Education and Sport Sciences and Health Research Institute, University of Limerick, Castletroy, Co. Limerick, Ireland; Irish World Academy of Music and Dance, University of Limerick, Castletroy, Co. Limerick, 
          Ireland},
          abbrev_source_title = {J Dance Med Sci},
          title = {Exploring ownership of Irish traditional dance music: Heritage or property?},
          title = {Care to Dance and Dance to Care: The Development of an Interdisciplinary Education Programme in Social Care and Dance/Movement},
          affiliations = {Munster Academy of Dance, Ireland; Technological University of the Shannon, Limerick, Ireland},
          title = {Dance exposure, general health, sleep and injury in elite adolescent Irish dancers: A prospective study},
          title = {Steps, style and sensing the difference: transmission and the re-contextualisation of Molyneaux’s traditional set dances within the Irish traditional dance competitive arena},
          journal = {Research in Dance Education},
          affiliations = {The Irish World Academy of Music and Dance, University of Limerick, Limerick, Ireland},
          correspondence_address = {C.E. Foley; The Irish World Academy of Music and Dance, University of Limerick, Limerick, Ireland; email: catherine.e.foley@ul.ie},
          abbrev_source_title = {Res. Dance Educ.},
          title = {‘Take Her Out and Air Her’: Irish Dances as Arranged by Stanford and Grainger},
          journal = {Musicology Australia},
          affiliations = {Department of Creative Arts, Media and Music, Dundalk Institute of Technology, Dundalk, Ireland},
          correspondence_address = {A. Commins; Department of Creative Arts, Media and Music, Dundalk Institute of Technology, Dundalk, Ireland; email: adele.commins@dkit.ie},
          abbrev_source_title = {Musicol. Aust.},
          title = {Dancing enriched whiteness: race and gender in commercial Irish dance performance from Riverdance to the Trump Inaugural Ball},
          affiliations = {Division of Dance, Texas Woman’s University, Denton, TX, United States},
          correspondence_address = {K. Holt; Division of Dance, Texas Woman’s University, Denton, United States; email: kholt7@twu.edu},
          title = {Contesting and negotiating hegemonic discourses: Constructing and developing a master’s programme in Irish traditional dance performance within a university context},
          title = {Complete Irish dancer: Optimization of health and performance in Irish dancers},
          journal = {Complete Irish Dancer: Optimization of Health and Performance in Irish Dancers},
          abbrev_source_title = {Complet. Ir. Danc.: Optim. of Health and Perform. in Ir. Dancers},
          title = {Music to Our Ears: Are Dancers at Risk for High Sound Level Exposure?},
          title = {PERFORMED IDENTITY: A Case Study in Irish Dance},
          title = {Traditional dances and their characteristic injury profiles. Systematic review},
          title = {Music, Songs, and Dances in Friel’s Plays: A Cultural Perspective},
  
- searches for any string that matches dance or music (| is or and called an infix operator)
  
  
      grep -i "\<dance\>" scopus.bib or grep -wi "dance" scopus.bib
          scopus.bib:     title = {Characteristics of Eight Irish Dance Landings Considerations for Training and Overuse Injury Prevention},
          scopus.bib:     journal = {Journal of Dance Medicine and Science},
          scopus.bib:     abbrev_source_title = {J Dance Med Sci},
          scopus.bib:     title = {The time-continuous association between turnout and axial joint moments in the competitive Irish dance ‘fly’ landing},
          scopus.bib:     journal = {Journal of Dance Medicine and Science},
          scopus.bib:     affiliations = {University of Roehampton, London, United Kingdom; School of Allied Health and Health Research Institute, University of Limerick, Castletroy, Co. Limerick, Ireland; Department of Physical Education and Sport Sciences and Health Research Institute, University of Limerick, Castletroy, Co. Limerick, Ireland; Irish World Academy of Music and Dance, University of Limerick, Castletroy, Co. Limerick, Ireland},
          scopus.bib:     abbrev_source_title = {J Dance Med Sci},
          scopus.bib:     title = {Exploring ownership of Irish traditional dance music: Heritage or property?},
          scopus.bib:     title = {Care to Dance and Dance to Care: The Development of an Interdisciplinary Education Programme in Social Care and Dance/Movement},
          scopus.bib:     affiliations = {Munster Academy of Dance, Ireland; Technological University of the Shannon, Limerick, Ireland},
          scopus.bib:     title = {Dance exposure, general health, sleep and injury in elite adolescent Irish dancers: A prospective study},
          scopus.bib:     title = {Steps, style and sensing the difference: transmission and the re-contextualisation of Molyneaux’s traditional set dances within the Irish traditional dance competitive arena},
          scopus.bib:     journal = {Research in Dance Education},
          scopus.bib:     affiliations = {The Irish World Academy of Music and Dance, University of Limerick, Limerick, Ireland},
          scopus.bib:     correspondence_address = {C.E. Foley; The Irish World Academy of Music and Dance, University of Limerick, Limerick, Ireland; email: catherine.e.foley@ul.ie},
          scopus.bib:     abbrev_source_title = {Res. Dance Educ.},
          scopus.bib:     title = {Dancing enriched whiteness: race and gender in commercial Irish dance performance from Riverdance to the Trump Inaugural Ball},
          scopus.bib:     affiliations = {Division of Dance, Texas Woman’s University, Denton, TX, United States},
          scopus.bib:     correspondence_address = {K. Holt; Division of Dance, Texas Woman’s University, Denton, United States; email: kholt7@twu.edu},
          scopus.bib:     title = {Contesting and negotiating hegemonic discourses: Constructing and developing a master’s programme in Irish traditional dance performance within a university context},
          scopus.bib:     title = {PERFORMED IDENTITY: A Case Study in Irish Dance},
          grep: or: No such file or directory
          grep: grep: No such file or directory
          grep: dance: No such file or directory
          scopus.bib:     title = {Characteristics of Eight Irish Dance Landings Considerations for Training and Overuse Injury Prevention},
          scopus.bib:     journal = {Journal of Dance Medicine and Science},
          scopus.bib:     abbrev_source_title = {J Dance Med Sci},
          scopus.bib:     title = {The time-continuous association between turnout and axial joint moments in the competitive Irish dance ‘fly’ landing},
          scopus.bib:     journal = {Journal of Dance Medicine and Science},
          scopus.bib:     affiliations = {University of Roehampton, London, United Kingdom; School of Allied Health and Health Research Institute, University of Limerick, Castletroy, Co. Limerick, Ireland; Department of Physical Education and Sport Sciences and Health Research Institute, University of Limerick, Castletroy, Co. Limerick, Ireland; Irish World Academy of Music and Dance, University of Limerick, Castletroy, Co. Limerick, Ireland},
          scopus.bib:     abbrev_source_title = {J Dance Med Sci},
          scopus.bib:     title = {Exploring ownership of Irish traditional dance music: Heritage or property?},
          scopus.bib:     title = {Care to Dance and Dance to Care: The Development of an Interdisciplinary Education Programme in Social Care and Dance/Movement},
          scopus.bib:     affiliations = {Munster Academy of Dance, Ireland; Technological University of the Shannon, Limerick, Ireland},
          scopus.bib:     title = {Dance exposure, general health, sleep and injury in elite adolescent Irish dancers: A prospective study},
          scopus.bib:     title = {Steps, style and sensing the difference: transmission and the re-contextualisation of Molyneaux’s traditional set dances within the Irish traditional dance competitive arena},
          scopus.bib:     journal = {Research in Dance Education},
          scopus.bib:     affiliations = {The Irish World Academy of Music and Dance, University of Limerick, Limerick, Ireland},
          scopus.bib:     correspondence_address = {C.E. Foley; The Irish World Academy of Music and Dance, University of Limerick, Limerick, Ireland; email: catherine.e.foley@ul.ie},
          scopus.bib:     abbrev_source_title = {Res. Dance Educ.},
          scopus.bib:     title = {Dancing enriched whiteness: race and gender in commercial Irish dance performance from Riverdance to the Trump Inaugural Ball},
          scopus.bib:     affiliations = {Division of Dance, Texas Woman’s University, Denton, TX, United States},
          scopus.bib:     correspondence_address = {K. Holt; Division of Dance, Texas Woman’s University, Denton, United States; email: kholt7@twu.edu},
          scopus.bib:     title = {Contesting and negotiating hegemonic discourses: Constructing and developing a master’s programme in Irish traditional dance performance within a university context},
          scopus.bib:     title = {PERFORMED IDENTITY: A Case Study in Irish Dance},
   
- searches for only whole words with \<word\> or -w

## Advanced Commands

      grep -i "dance" -A2 scopus.bib
            title = {Characteristics of Eight Irish Dance Landings Considerations for Training and Overuse Injury Prevention},
            year = {2021},
            journal = {Journal of Dance Medicine and Science},
            volume = {25},
            number = {1},
    --
            abbrev_source_title = {J Dance Med Sci},
            type = {Article},
            publication_stage = {Final},
    --
            title = {The time-continuous association between turnout and axial joint moments in the competitive Irish dance ‘fly’ landing},
            year = {2021},
            journal = {Sports Biomechanics},
    --
            title = {Dietary Intake, Body Composition, and Nutrition Knowledge of Irish Dancers},
            year = {2020},
            journal = {Journal of Dance Medicine and Science},
            volume = {24},
            number = {3},
    --
            affiliations = {University of Roehampton, London, United Kingdom; School of Allied Health and Health Research Institute, University of Limerick, Castletroy, Co. Limerick, Ireland; Department of Physical Education and Sport Sciences and Health Research Institute, University of Limerick, Castletroy, Co. Limerick, Ireland; Irish World Academy of Music and Dance, University of Limerick, Castletroy, Co. Limerick, Ireland},
            correspondence_address = {J. Challis; University of Roehampton, London, United Kingdom; email: jasminechallisl@gmail.com},
            publisher = {SAGE Publications Ltd},
    --
            abbrev_source_title = {J Dance Med Sci},
            type = {Article},
            publication_stage = {Final},
    --
            title = {Exploring ownership of Irish traditional dance music: Heritage or property?},
            year = {2022},
            journal = {International Journal of Cultural Property},
    --
            title = {Care to Dance and Dance to Care: The Development of an Interdisciplinary Education Programme in Social Care and Dance/Movement},
            year = {2023},
            journal = {Global Perspectives on Probing Narratives in Healthcare},
    --
            affiliations = {Munster Academy of Dance, Ireland; Technological University of the Shannon, Limerick, Ireland},
            publisher = {IGI Global},
            isbn = {978-166848065-6; 978-166848064-9},
    --
            title = {Dance exposure, general health, sleep and injury in elite adolescent Irish dancers: A prospective study},
            year = {2019},
            journal = {Physical Therapy in Sport},
    --
            title = {Steps, style and sensing the difference: transmission and the re-contextualisation of Molyneaux’s traditional set dances within the Irish traditional dance competitive arena},
            year = {2020},
            journal = {Research in Dance Education},
            volume = {21},
            number = {3},
    --
            affiliations = {The Irish World Academy of Music and Dance, University of Limerick, Limerick, Ireland},
            correspondence_address = {C.E. Foley; The Irish World Academy of Music and Dance, University of Limerick, Limerick, Ireland; email: catherine.e.foley@ul.ie},
            publisher = {Routledge},
            issn = {14647893},
    --
            abbrev_source_title = {Res. Dance Educ.},
            type = {Article},
            publication_stage = {Final},
    --
            title = {‘Take Her Out and Air Her’: Irish Dances as Arranged by Stanford and Grainger},
            year = {2023},
            journal = {Musicology Australia},
    --
            title = {Dancing enriched whiteness: race and gender in commercial Irish dance performance from Riverdance to the Trump Inaugural Ball},
            year = {2023},
            journal = {Irish Studies Review},
    --
            affiliations = {Division of Dance, Texas Woman’s University, Denton, TX, United States},
            correspondence_address = {K. Holt; Division of Dance, Texas Woman’s University, Denton, United States; email: kholt7@twu.edu},
            publisher = {Routledge},
            issn = {09670882},
    --
            title = {Contesting and negotiating hegemonic discourses: Constructing and developing a master’s programme in Irish traditional dance performance within a university context},
            year = {2021},
            journal = {The Artist and Academia},
    --
            title = {Complete Irish dancer: Optimization of health and performance in Irish dancers},
            year = {2020},
            journal = {Complete Irish Dancer: Optimization of Health and Performance in Irish Dancers},
            pages = {1 – 278},
            url = {https://www.scopus.com/inward/record.uri?eid=2-s2.0-85145427207&partnerID=40&md5=1c8be1c09150f627c4045e61ebb0a875},
    --
            abbrev_source_title = {Complet. Ir. Danc.: Optim. of Health and Perform. in Ir. Dancers},
            type = {Book},
            publication_stage = {Final},
    --
            title = {Music to Our Ears: Are Dancers at Risk for High Sound Level Exposure?},
            year = {2020},
            journal = {Medical Problems of Performing Artists},
    --
            title = {PERFORMED IDENTITY: A Case Study in Irish Dance},
            year = {2023},
            journal = {The Routledge Companion to the Anthropology of Performance},
    --
            title = {Traditional dances and their characteristic injury profiles. Systematic review},
            year = {2020},
            journal = {Apunts. Educacion Fisica y Deportes},
    --
            title = {Music, Songs, and Dances in Friel’s Plays: A Cultural Perspective},
            year = {2022},
            journal = {Theory and Practice in Language Studies},
            
- prints the matching line plus the two lines after with -A2
  
  
      grep -i "dance" -B2 scopus.bib
          @ARTICLE{Christensen202130,
                author = {Christensen, Sarah Klopp and Johnson, Aaron Wayne and Van Wagoner, Natalie and Corey, Taryn E. and McClung, Matthew S. and Hunter, Iain},
                title = {Characteristics of Eight Irish Dance Landings Considerations for Training and Overuse Injury Prevention},
                year = {2021},
                journal = {Journal of Dance Medicine and Science},
        --
                pmid = {33706853},
                language = {English},
                abbrev_source_title = {J Dance Med Sci},
        --
        @ARTICLE{Wallace2021,
                author = {Wallace, Kelsi and Kalogeropoulou, Sofia and Lamb, Peter},
                title = {The time-continuous association between turnout and axial joint moments in the competitive Irish dance ‘fly’ landing},
        --
        @ARTICLE{Challis2020105,
                author = {Challis, Jasmine and Cahalan, Roisin and Jakeman, Phil and NiBhriain, Orfhlaith and Cronin, Linda and Reeves, Sue},
                title = {Dietary Intake, Body Composition, and Nutrition Knowledge of Irish Dancers},
                year = {2020},
                journal = {Journal of Dance Medicine and Science},
        --
                doi = {10.12678/1089-313X.24.3.105},
                url = {https://www.scopus.com/inward/record.uri?eid=2-s2.0-85090103258&doi=10.12678%2f1089-313X.24.3.105&partnerID=40&md5=c93102193cb70750c325e60d43940625},
                affiliations = {University of Roehampton, London, United Kingdom; School of Allied Health and Health Research Institute, University of Limerick, Castletroy, Co. Limerick, Ireland; Department of Physical Education and Sport Sciences and Health Research Institute, University of Limerick, Castletroy, Co. Limerick, Ireland; Irish World Academy of Music and Dance, University of Limerick, Castletroy, Co. Limerick, Ireland},
        --
                pmid = {32867912},
                language = {English},
                abbrev_source_title = {J Dance Med Sci},
        --
        @ARTICLE{McDonagh2022183,
                author = {McDonagh, Luke},
                title = {Exploring ownership of Irish traditional dance music: Heritage or property?},
        --
        @BOOK{McKenna2023263,
                author = {McKenna, Carmel and Stritch, Jennifer Moran},
                title = {Care to Dance and Dance to Care: The Development of an Interdisciplinary Education Programme in Social Care and Dance/Movement},
        --
                doi = {10.4018/978-1-6684-8064-9.ch016},
                url = {https://www.scopus.com/inward/record.uri?eid=2-s2.0-85167773937&doi=10.4018%2f978-1-6684-8064-9.ch016&partnerID=40&md5=ca1faeb3ff1431034bda8c5f51521d8c},
                affiliations = {Munster Academy of Dance, Ireland; Technological University of the Shannon, Limerick, Ireland},
        --
        @ARTICLE{Cahalan2019153,
                author = {Cahalan, Roisin and Bargary, Norma and O'Sullivan, Kieran},
                title = {Dance exposure, general health, sleep and injury in elite adolescent Irish dancers: A prospective study},
        --
        @ARTICLE{Foley2020312,
                author = {Foley, Catherine E.},
                title = {Steps, style and sensing the difference: transmission and the re-contextualisation of Molyneaux’s traditional set dances within the Irish traditional dance competitive arena},
                year = {2020},
                journal = {Research in Dance Education},
        --
                doi = {10.1080/14647893.2020.1776242},
                url = {https://www.scopus.com/inward/record.uri?eid=2-s2.0-85087516671&doi=10.1080%2f14647893.2020.1776242&partnerID=40&md5=18a94e1210cc85d652a622a8503eb527},
                affiliations = {The Irish World Academy of Music and Dance, University of Limerick, Limerick, Ireland},
                correspondence_address = {C.E. Foley; The Irish World Academy of Music and Dance, University of Limerick, Limerick, Ireland; email: catherine.e.foley@ul.ie},
        --
                issn = {14647893},
                language = {English},
                abbrev_source_title = {Res. Dance Educ.},
        --
        @ARTICLE{Commins202322,
                author = {Commins, Adèle},
                title = {‘Take Her Out and Air Her’: Irish Dances as Arranged by Stanford and Grainger},
        --
        @ARTICLE{Holt2023502,
                author = {Holt, Kathryn},
                title = {Dancing enriched whiteness: race and gender in commercial Irish dance performance from Riverdance to the Trump Inaugural Ball},
        --
                doi = {10.1080/09670882.2023.2268549},
                url = {https://www.scopus.com/inward/record.uri?eid=2-s2.0-85174285738&doi=10.1080%2f09670882.2023.2268549&partnerID=40&md5=aacaf73eb65129a11d8d628d023e3aa1},
                affiliations = {Division of Dance, Texas Woman’s University, Denton, TX, United States},
                correspondence_address = {K. Holt; Division of Dance, Texas Woman’s University, Denton, United States; email: kholt7@twu.edu},
        --
        @BOOK{Foley2021181,
                author = {Foley, Catherine E.},
                title = {Contesting and negotiating hegemonic discourses: Constructing and developing a master’s programme in Irish traditional dance performance within a university context},
        --
        @BOOK{Cahalan20201,
                author = {Cahalan, Róisín},
                title = {Complete Irish dancer: Optimization of health and performance in Irish dancers},
                year = {2020},
                journal = {Complete Irish Dancer: Optimization of Health and Performance in Irish Dancers},
        --
                isbn = {978-153617389-5},
                language = {English},
                abbrev_source_title = {Complet. Ir. Danc.: Optim. of Health and Perform. in Ir. Dancers},
        --
        @ARTICLE{Busenbarrick2020227,
                author = {Busenbarrick, Haley and Davenport, Kathleen L.},
                title = {Music to Our Ears: Are Dancers at Risk for High Sound Level Exposure?},
        --
        @BOOK{de Gallaí2023267,
                author = {de Gallaí, Breandán},
                title = {PERFORMED IDENTITY: A Case Study in Irish Dance},
        --
        @ARTICLE{Taboada-Iglesias20201,
                author = {Taboada-Iglesias, Yaiza and Abalo-Núñez, Rocío and García-Remeseiro, Tania},
                title = {Traditional dances and their characteristic injury profiles. Systematic review},
        --
        @ARTICLE{Kitishat20222090,
                author = {Kitishat, Amal Riyadh},
                title = {Music, Songs, and Dances in Friel’s Plays: A Cultural Perspective},
        - prints the matching line plus the two lines before with -B2
  
  
          grep -i -m1 "music" scopus.bib
              affiliations = {University of Roehampton, London, United Kingdom; School of Allied Health and Health Research Institute, University of Limerick, Castletroy, Co. Limerick, Ireland; Department of Physical     Education and Sport Sciences and Health Research Institute, University of Limerick, Castletroy, Co. Limerick, Ireland; Irish World Academy of Music and Dance, University of Limerick, Castletroy, Co. Limerick, Ireland},
    
    - returns search for music and stops after the first hit
    
          grep -in "music" scopus.bib
            78:     affiliations = {University of Roehampton, London, United Kingdom; School of Allied Health and Health Research Institute, University of Limerick, Castletroy, Co. Limerick, Ireland; Department of Physical Education and Sport Sciences and Health Research Institute, University of Limerick, Castletroy, Co. Limerick, Ireland; Irish World Academy of Music and Dance, University of Limerick, Castletroy, Co. Limerick, Ireland},
            114:    title = {Exploring ownership of Irish traditional dance music: Heritage or property?},
            204:    affiliations = {The Irish World Academy of Music and Dance, University of Limerick, Limerick, Ireland},
            205:    correspondence_address = {C.E. Foley; The Irish World Academy of Music and Dance, University of Limerick, Limerick, Ireland; email: catherine.e.foley@ul.ie},
            220:    journal = {Musicology Australia},
            226:    affiliations = {Department of Creative Arts, Media and Music, Dundalk Institute of Technology, Dundalk, Ireland},
            227:    correspondence_address = {A. Commins; Department of Creative Arts, Media and Music, Dundalk Institute of Technology, Dundalk, Ireland; email: adele.commins@dkit.ie},
            231:    abbrev_source_title = {Musicol. Aust.},
            299:    title = {Music to Our Ears: Are Dancers at Risk for High Sound Level Exposure?},
            401:    title = {Music, Songs, and Dances in Friel’s Plays: A Cultural Perspective},
        
- returns the line numbers for each hit
  
      grep -Eiw "[a-z]{10}" scopus.bib
                    title = {Irish Dancing Injuries and Associated Risk Factors: A Systematic Review},
                  affiliations = {Egas Moniz School of Health and Science, Almada, 2829-511, Portugal; Hospital Garcia de Orta, Almada, 2805-267, Portugal; CiiEM—Centro de Investigação Interdisciplinar Egas Moniz, Caparica, 2829-511, Portugal; La Trobe Sport and Exercise Medicine Research Centre, La Trobe University, Melbourne, 3086, Australia; The Australian Ballet, Melbourne, 3006, Australia; Interdisciplinary Centre for the Study of Human Performance, Neuromuscular Research Lab, Human Kinetics Faculty, University of Lisbon, Cruz Quebrada-Dafundo, 1499-002, Portugal},
                  publisher = {Multidisciplinary Digital Publishing Institute (MDPI)},
                  title = {Characteristics of Eight Irish Dance Landings Considerations for Training and Overuse Injury Prevention},
                  affiliations = {Department of Exercise Sciences, Brigham Young University, Provo, UT, United States},
                  correspondence_address = {A.W. Johnson; Department of Exercise Sciences, Brigham Young University, Provo, United States; email: wayne_johnson@byu.edu},
                  title = {The time-continuous association between turnout and axial joint moments in the competitive Irish dance ‘fly’ landing},
                  affiliations = {School of Physical Education, Sport and Exercise Sciences, University of Otago, Dunedin, New Zealand; School of Performing Arts, University of Otago, Dunedin, New Zealand},
                  correspondence_address = {P. Lamb; School of Physical Education, Sport and Exercise Sciences, University of Otago, Dunedin, New Zealand; email: peter.lamb@otago.ac.nz},
                  affiliations = {University of Roehampton, London, United Kingdom; School of Allied Health and Health Research Institute, University of Limerick, Castletroy, Co. Limerick, Ireland; Department of Physical Education and Sport Sciences and Health Research Institute, University of Limerick, Castletroy, Co. Limerick, Ireland; Irish World Academy of Music and Dance, University of Limerick, Castletroy, Co. Limerick, Ireland},
                  correspondence_address = {J. Challis; University of Roehampton, London, United Kingdom; email: jasminechallisl@gmail.com},
                  author = {Bevilacqua, Roberta and Benadduci, Marco and Bonfigli, Anna Rita and Riccardi, Giovanni Renato and Melone, Giovanni and La Forgia, Angela and Macchiarulo, Nicola and Rossetti, Luca and Marzorati, Mauro and Rizzo, Giovanna and Di Bitonto, Pierpaolo and Potenza, Ada and Fiorini, Laura and Cortellessa Loizzo, Federica Gabriella and La Viola, Carlo and Cavallo, Filippo and Leone, Alessandro and Rescio, Gabriele and Caroppo, Andrea and Manni, Andrea and Cesta, Amedeo and Cortellessa, Gabriella and Fracasso, Francesca and Orlandini, Andrea and Umbrico, Alessandro and Rossi, Lorena and Maranesi, Elvira},
                  affiliations = {Scientific Direction, IRCCS INRCA, Ancona, Italy; Clinical Unit of Physical Rehabilitation, IRCCS INRCA, Ancona, Italy; Innovation Lab, Innovation, Marketing and Technology, Exprivia S.p.A., Molfetta, Italy; Consiglio Nazionale delle Ricerche, Istituto di Tecnologie Biomediche, Milan, Italy; Grifo Multimedia Srl, Bari, Italy; Dipartimento Ingegneria Industriale, Università degli Studi di Firenze, Firenze, Italy; Istituto di BioRobotica, Scuola Superiore Sant'Anna, Pontedera, Italy; Consiglio Nazionale delle Ricerche, Istituto per la Microelettronica e i Microsistemi, Lecce, Italy; Consiglio Nazionale delle Ricerche, Istituto di Scienze e Tecnologie della Cognizione, Rome, Italy},
                  correspondence_address = {F. Fracasso; Consiglio Nazionale delle Ricerche, Istituto di Scienze e Tecnologie della Cognizione, Rome, Italy; email: francesca.fracasso@istc.cnr.it},
                  publisher = {Cambridge University Press},
                  affiliations = {Moscow, Russian Federation},
                  journal = {Global Perspectives on Probing Narratives in Healthcare},
                  affiliations = {Munster Academy of Dance, Ireland; Technological University of the Shannon, Limerick, Ireland},
                  abbrev_source_title = {Global Perspectives on Probing Narratives in Healthc.},
                  title = {Dance exposure, general health, sleep and injury in elite adolescent Irish dancers: A prospective study},
                  affiliations = {School of Allied Health, University of Limerick, Limerick, Ireland; Health Research Institute, University of Limerick, Limerick, Ireland; Department of Mathematics & Statistics, University of Limerick, Limerick, Ireland; Sports Spine Centre, Aspetar Sports Medicine and Orthopaedic Hospital, Doha, Qatar; Ageing Research Centre, Health Research Institute, University of Limerick, Limerick, Ireland},
                  correspondence_address = {R. Cahalan; School of Allied Health, University of Limerick, Limerick, Ireland; email: roisin.cahalan@ul.ie},
                  title = {Steps, style and sensing the difference: transmission and the re-contextualisation of Molyneaux’s traditional set dances within the Irish traditional dance competitive arena},
                  affiliations = {The Irish World Academy of Music and Dance, University of Limerick, Limerick, Ireland},
                  correspondence_address = {C.E. Foley; The Irish World Academy of Music and Dance, University of Limerick, Limerick, Ireland; email: catherine.e.foley@ul.ie},
                  journal = {Musicology Australia},
                  affiliations = {Department of Creative Arts, Media and Music, Dundalk Institute of Technology, Dundalk, Ireland},
                  correspondence_address = {A. Commins; Department of Creative Arts, Media and Music, Dundalk Institute of Technology, Dundalk, Ireland; email: adele.commins@dkit.ie},
                  title = {Dancing enriched whiteness: race and gender in commercial Irish dance performance from Riverdance to the Trump Inaugural Ball},
                  affiliations = {Division of Dance, Texas Woman’s University, Denton, TX, United States},
                  correspondence_address = {K. Holt; Division of Dance, Texas Woman’s University, Denton, United States; email: kholt7@twu.edu},
                  title = {Contesting and negotiating hegemonic discourses: Constructing and developing a master’s programme in Irish traditional dance performance within a university context},
                  affiliations = {University of Limerick, Ireland},
                  affiliations = {School of Allied Health, University of Limerick, Limerick, Ireland; Physical Activity for Health Research Cluster, University of Limerick, Limerick, Ireland},
                  publisher = {Nova Science Publishers, Inc.},
                  journal = {Medical Problems of Performing Artists},
                  correspondence_address = {K.L. Davenport; Hospital for Special Surgery, Florida, 300 Palm Beach Lakes Blvd., West Palm Beach, 33401, United States; email: davenportk@hss.edu},
                  type = {Conference paper},
                  affiliations = {Texas Tech University, United States; University of Minnesota, Duluth, United States},
          @CONFERENCE{Bevilacqua2022,
                  author = {Bevilacqua, Roberta and Benadduci, Marco and Riccardi, Giovanni Renato and Melone, Giovanni and La Forgia, Angela and MacChiarulo, Nicola and Rossetti, Luca and Marzorati, Mauro and Rizzo, Giovanna and Di Bitonto, Pierpaolo and Potenza, Ada and Fiorini, Laura and Loizzo, Federica Gabriella Cornacchia and La Viola, Carlo and Cavallo, Filippo and Leone, Alessandro and Rescio, Gabriele and Caroppo, Andrea and Manni, Andrea and Cesta, Amedeo and Cortellessa, Gabriella and Fracasso, Francesca and Orlandini, Andrea and Umbrico, Alessandro and Amabili, Giulio and Rossi, Lorena and Maranesi, Elvira},
                  affiliations = {Scientific Direction, IRCCS INRCA, Ancona, Italy; Clinical Unit of Physical Rehabilitation, IRCCS INRCA, Ancona, Italy; Exprivia S.p.a., Innovation Lab, Innovation, Marketing & Technology, Molfetta (BA), Italy; Consiglio Nazionale Delle Ricerche, Istituto di Tecnologie Biomediche (ITB), Milano, Italy; Dipartimento Ingegneria Industriale, Università Degli Studi di Firenze, Firenze, Italy; Istituto di BioRobotica, Scuola Superiore sant'Anna, (PI), Pontedera, Italy; Dipartimento Ingegneria Industriale, Universita Degli Studi di Firenze, Firenze, Italy; Consiglio Nazionale Delle Ricerche, Istituto per la Microelettronica e i Microsistemi, Lecce, Italy; Consiglio Nazionale Delle Ricerche, Istituto di Scienze e Tecnologie per la Cognizione, Roma, Italy; Grifo Multimedia Srl, Bari, Italy},
                  editor = {Bevilacqua R. and Fiorini L. and Fracasso F. and Umbrico A. and Wieching R.},
                  type = {Conference paper},
                  affiliations = {University of Limerick, Ireland},
                  title = {Traditional dances and their characteristic injury profiles. Systematic review},
                  affiliations = {Faculty of Physical Therapy, University of Vigo, Spain; Research Group GIES-10(DE-3), Instituto de Investigación Sanitaria Galicia Sur (IIS Galicia Sur), SERGASUVIGO, Spain},
                  correspondence_address = {Y. Taboada-Iglesias; Faculty of Physical Therapy, University of Vigo, Spain; email: yaitaboada@uvigo.es},
                  affiliations = {Department of English, Ajloun College, Al Balqa Applied University, Ajloun, Jordan},
          
- returns any five letter words that contain the characters a-z
  
  
      grep -Eiw "m.{3}s" scopus.bib
          no result
  
- returns any words that start with m and end with s and have three letters in the middle due to the {3}
  
  
      grep -Eio "^dance(A|B)[A-Z]*" scopus.bib | sort | uniq -c
          no result
  
- orders the sort output alphabetically, uniq deduplicates results, and -c counts the number of duplicates
  

## More Commands
cut - takes results of grep and removes the first column based on the comma as the column delimiter

sed - takes results and replaces sections 

awk - searches files to see if they contain lines that match with the specified patterns and then performs the associated actions
