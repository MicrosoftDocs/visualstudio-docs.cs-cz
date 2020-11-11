---
title: Začínáme s tvorbou her pomocí platformy Unity
description: Začínáme s Unity a Visual Studio pro Mac
author: heiligerdankgesang
ms.author: dominicn
ms.date: 11/09/2020
ms.technology: vs-ide-general
ms.assetid: D07FA43B-9D18-4DFA-8343-CD538FAD84DB
ms.topic: how-to
ms.openlocfilehash: cae68b54623564028ea85dd1aa319fad5ceaec48
ms.sourcegitcommit: 2cf3a03044592367191b836b9d19028768141470
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/11/2020
ms.locfileid: "94493579"
---
# <a name="getting-started-building-games-with-unity-in-visual-studio-for-mac"></a>Začínáme s vytvářením her v Unity v Visual Studio pro Mac

Unity je herní stroj, který umožňuje vyvíjet hry v jazyce C#. Tento návod ukazuje, jak začít s vývojem a laděním her v Unity pomocí Visual Studio pro Mac a Visual Studio pro Mac nástrojů pro rozšíření Unity společně s prostředím Unity.

Visual Studio pro Mac Tools for Unity je bezplatné rozšíření instalované s Visual Studio pro Mac. Umožňuje vývojářům Unity využít výhody funkcí Visual Studio pro Mac, včetně skvělé podpory technologie IntelliSense, funkcí ladění a dalších.

## <a name="objectives"></a>Cíle

> [!div class="checklist"]
> * Další informace o vývoji Unity pomocí Visual Studio pro Mac

## <a name="prerequisites"></a>Předpoklady

- Visual Studio pro Mac ( [https://www.visualstudio.com/vs/mac](https://www.visualstudio.com/vs/visual-studio-mac) )
- Unity 5.6.1 Personal Edition nebo vyšší ( [https://store.unity.com](https://store.unity.com/) , vyžaduje spuštění účtu Unity.com)

## <a name="intended-audience"></a>Zamýšlená cílová skupina

Toto testovací prostředí je určené pro vývojáře, kteří znají jazyk C#, ale hloubkové prostředí není nutné.

## <a name="task-1-creating-a-basic-unity-project"></a>Úloha 1: Vytvoření základního projektu Unity

1. Spusťte **Unity**. Přihlaste se, pokud je požadováno.

2. Klikněte na **Nový**.

    ![Nové tlačítko v Unity](media/unity-image1.png)

3. Nastavte **název projektu** na **"UnityLab"** a vyberte **3D**. Klikněte na **vytvořit projekt**.

    ![obrazovka pro vytvoření nového projektu](media/unity-image2.png)

4. Nyní se díváte na výchozí rozhraní Unity. Má hierarchii scény s herními objekty vlevo, prostorové zobrazení prázdné scény zobrazené uprostřed, podokno soubory projektu dole a kontrolor a služby na pravé straně. Samozřejmě existuje mnohem více dalších funkcí, než je to, ale ty jsou několika důležitějšími součástmi.

    ![prázdné rozhraní Unity](media/unity-image3.png)

5. Pro vývojáře, kteří jsou v Unity, všechno, co běží ve vaší aplikaci, bude existovat v kontextu **scény**. Soubor scény je jeden soubor, který obsahuje nejrůznější metadata o prostředcích použitých v projektu pro aktuální scénu a její vlastnosti. Když zabalíte aplikaci pro platformu, výsledná aplikace bude mít na výběr jednu nebo více scén, a to i jakýkoli kód závislý na platformě, který přidáte. V projektu můžete mít tolik scén, kolik jich je potřeba.

6. Nová scéna má pouze fotoaparát a směrové světlo. Scéna vyžaduje, aby **kamera** mohla být viditelná a **naslouchací proces zvuku** , který by měl být zvukem. Tyto součásti jsou připojené k **GameObject**.

7. Vyberte objekt **hlavní kamery** z podokna **hierarchie** .

    ![objekt hlavní kamery zvýrazněný v podokně hierarchie](media/unity-image4.png)

8. Vyberte podokno **inspektora** na pravé straně okna a zkontrolujte jeho vlastnosti. Mezi vlastnosti kamery patří transformace informace, pozadí, typ projekce, pole zobrazení a tak dále. Ve výchozím nastavení se přidala taky součást pro naslouchací proces zvuku, která v podstatě vykresluje zvuk scény z virtuálního mikrofonu připojeného ke kameře.

    ![podokno inspektoru](media/unity-image5.png)

9. Vyberte objekt **směrového světla** . To poskytuje světlo pro scénu, aby komponenty jako shadery věděli, jak vykreslovat objekty.

    ![objekt směru světla zvýrazněný](media/unity-image6.png)

10. Pomocí **inspektoru** můžete vidět, že zahrnuje běžné vlastnosti osvětlení včetně typu, barvy, intenzity, typu stínu atd.

    ![prohlížení vlastností v podokně kontrola](media/unity-image7.png)

11. Je důležité, abyste odkazovali na to, že projekty v Unity jsou trochu odlišné od jejich Visual Studio pro Mac protějšků. Na kartě **projekt** dole klikněte pravým tlačítkem myši na složku **assety** a vyberte **Zobrazit ve Finderu**.

    ![zobrazit kontextovou akci vyhledávacího kontextu](media/unity-image8.png)

12. Projekty obsahují **prostředky** , **knihovny** , **ProjectSettings** a **dočasné** složky, jak vidíte. Pouze ten, který se zobrazí v rozhraní, je složka **assets** . Složka **Library (knihovna** ) je místní mezipaměť pro importované prostředky; obsahuje všechna metadata pro prostředky. Složka **ProjectSettings** ukládá nastavení, která můžete konfigurovat. Dočasná **Složka se používá pro dočasné soubory** z mono a Unity během procesu sestavení. Existuje také soubor řešení, který můžete otevřít v Visual Studio pro Mac ( **UnityLab. sln** ).

    ![assety ve Finderu](media/unity-image9.png)

13. Zavřete okno **hledání** a vraťte se do **Unity**.

14. Složka **assets (prostředky** ) obsahuje všechny vaše prostředky – umění, kód, zvuk atd. V tuto chvíli je teď prázdné, ale tady se každý soubor, který do projektu přinesete, doprovází. To je vždy složka nejvyšší úrovně v **editoru Unity**. Vždy ale přidávejte a odstraňujte soubory prostřednictvím rozhraní Unity (nebo Visual Studio pro Mac), a ne přímo v systému souborů.

    ![Složka assets v Unity](media/unity-image10.png)

15. **GameObject** je centrální pro vývoj v Unity, protože téměř všechno jsou odvozeny od tohoto typu, včetně modelů, světel, částic a tak dále. Pomocí nabídky **GameObject > 3D objektu > Cube** přidejte do scény nový objekt **datové krychle** .

    ![objekt datové krychle ve scéně](media/unity-image11.png)

16. Přečtěte si stručný přehled vlastností nového **GameObject** a podívejte se, že má název, značku, vrstvu a transformaci. Tyto vlastnosti jsou společné pro všechny **GameObjects**. Kromě toho se k **datové krychli** připojilo několik komponent, které poskytují potřebné funkce, včetně filtru sítě, kolidujícího okna a zobrazovací jednotky.

    ![vlastnosti herního objektu](media/unity-image12.png)

17. Přejmenujte objekt **datové krychle** , který má ve výchozím nastavení název **"Cube** " na **"Enemy"**. Nezapomeňte tuto změnu uložit stisknutím klávesy **ENTER** . Toto bude Enemy krychle v naší jednoduché hře.

    ![vlastnost přejmenování objektu datové krychle](media/unity-image13.png)

18. Přidejte další objekt **datové krychle** do scény pomocí stejného procesu a pojmenujte ho **"aktér"**.

    ![přejmenovat druhý objekt datové krychle](media/unity-image14.png)

19. Označte objekt přehrávače také jako **"aktér"** (viz rozevírací seznam **značka** v části pole název). Použijeme ho ve skriptu Enemy, abychom pomohli najít objekt hry přehrávače.

    ![označení objektu Player](media/unity-image15.png)

20. V zobrazení **scény** přesuňte objekt Player pryč z objektu Enemy podél osy z pomocí myši. Podél osy Z můžete pohybovat výběrem a přetažením datové krychle podle **červeného** panelu směrem k **modré** čáře. Vzhledem k tomu, že datová krychle žije v prostorovém prostoru, ale dá se pokaždé přetáhnout jenom na 2D ose, na které táhnete, je obzvláště důležitá.

    ![zobrazení scény znázorňující krychli](media/unity-image16.png)

21. Přesuňte datovou krychli směrem dolů a doprava podél osy. Tím se v **inspektoru** aktualizuje vlastnost **Transform. Position** . Nezapomeňte na umístění, které se tady zobrazuje, podle toho, co se tady zobrazuje, abyste v testovacím prostředí usnadnili pozdější kroky.

    ![Přesunutí jedné krychle podél osy](media/unity-image17.png)

22. Nyní můžete přidat nějaký kód, který bude řídit logiku Enemy tak, aby vykonává hráč. V okně **projektu** klikněte pravým tlačítkem na složku **assets (prostředky** ) a vyberte **vytvořit > skript jazyka C#**.

    ![Akce kontextu skriptu jazyka C#](media/unity-image18.png)

23. Pojmenujte nový skript C# **"EnemyAI"**.

    ![Skript jazyka C#](media/unity-image19.png)

24. Chcete-li připojit skripty k herním objektům, přetáhněte nově vytvořený skript do objektu **Enemy** v podokně **hierarchie** . Objekt bude nyní používat chování z tohoto skriptu.

    ![zvýraznění znázorňující přidání skriptu do objektu hry](media/unity-image20.png)

25. Vyberte **soubor > Uložit scény** a uložte aktuální scénu. Pojmenujte ho **"MyScene"**.

## <a name="task-2-working-with-visual-studio-for-mac-tools-for-unity"></a>Úkol 2: práce s nástroji pro Visual Studio pro Mac pro Unity

1. Nejlepším způsobem, jak upravit kód v jazyce C#, je použít Visual Studio pro Mac. Můžete nakonfigurovat Unity pro použití Visual Studio pro Mac jako výchozí obslužné rutiny. Vyberte možnost **předvolby > Unity**.

2. Vyberte kartu **externí nástroje** . V rozevíracím seznamu **externí editor skriptů** vyberte **Procházet** a vyberte **aplikace/Visual Studio. app**. Případně, pokud již existuje možnost sady **Visual Studio** , stačí ji vybrat.

    ![karta externích nástrojů v předvolbách](media/unity-image21.png)

3. Unity je teď nakonfigurované na použití **Visual Studio pro Mac** pro úpravy skriptů. Zavřete dialogové okno **Předvolby Unity** .

    ![Předvolby sady Visual Studio vybrané v předvolbách](media/unity-image22.png)

4. Poklikejte na **EnemyAI.cs** a otevře se v **Visual Studio pro Mac**.

    ![Enemy Asset vybraný v Unity](media/unity-image23.png)

5. Řešení sady Visual Studio je jednoduché. Obsahuje složku **assets** (která je stejná jako u služby **Finder** ) a skript **EnemyAI.cs** , který jste vytvořili dříve. V propracovanějších projektech bude hierarchie pravděpodobně vypadat jinak, než co vidíte v Unity.

    ![Okno řešení v Visual Studio pro Mac](media/unity-image24.png)

6. **EnemyAI.cs** je otevřen v editoru. Počáteční skript obsahuje pouze zástupné procedury pro metody **Start** a **Update** .

7. Nahraďte počáteční kód Enemy kódem níže.

    ```csharp
    public class EnemyAI : MonoBehaviour
    {
        public float Speed = 50;
        private Transform _playerTransform;
        private Transform _myTransform;

        void Start()
        {
            var player = GameObject.FindGameObjectWithTag("Player");
            if (!player)
            {
                Debug.LogError(
                    "Could not find the main player. Ensure it has the player tag set.");
            }
            else
            {
                _playerTransform = player.transform;
            }
            _myTransform = this.transform;
        }

        void Update()
        {
            var moveAmount = Speed * Time.deltaTime;
            _myTransform.position = Vector3.MoveTowards(_myTransform.position,
                _playerTransform.position, moveAmount);

            if (_myTransform.position == _playerTransform.position)
            {
                _myTransform.position = Vector3.back * 10;
            }
        }
    }
    ```

8. Přečtěte si rychlý přehled jednoduchého Enemy chování, které je zde definované. V metodě **Start** získáme odkaz na objekt přehrávače (podle jeho značky) a také na jeho **transformaci**. V metodě **Update** , která se nazývá každý snímek, se Enemy přesune k objektu přehrávače. Klíčová slova a názvy používají barevné kódování, aby bylo snazší pochopit základ kódu v Visual Studio pro Mac.

9. Uložte změny do skriptu Enemy v **Visual Studio pro Mac**.

## <a name="task-3-debugging-the-unity-project"></a>Úkol 3: ladění projektu Unity

1. Nastavte zarážku na prvním řádku kódu v metodě **Start** . Můžete buď kliknout na okraj editoru na cílovém řádku, nebo umístit kurzor na řádek a stisknout klávesu **F9**.

    ![Nastavení zarážky v Visual Studio pro Mac](media/unity-image25.png)

2. Klikněte na tlačítko **Spustit ladění** nebo stiskněte klávesu **F5**. Tím se projekt sestaví a připojí k Unity pro ladění.

    ![tlačítko Start v Visual Studio pro Mac](media/unity-image26.png)

3. Vraťte se do **Unity** a kliknutím na tlačítko **Spustit** hru spusťte.

    ![tlačítko spustit v Unity](media/unity-image27.png)

4. Měla by být zarážka a teď můžete použít nástroje pro ladění Visual Studio pro Mac.

    ![pozice zarážky v Visual Studio pro Mac](media/unity-image28.png)

5. V okně **místní** hodnoty vyhledejte **Tento** ukazatel, který odkazuje na objekt **EnemyAI** . Rozbalte odkaz a podívejte se, že můžete procházet přidružené členy jako **rychlost**.

    ![Okno místní hodnoty v Visual Studio pro Mac](media/unity-image29.png)

6. Odeberte zarážku z metody **Start** stejným způsobem jako byl přidán – kliknutím na něj na okraji nebo výběrem řádku a stisknutím klávesy **F9**.

    ![Odebrání zarážky v Visual Studio pro Mac kliknutím na ni](media/unity-image30.png)

7. Stisknutím klávesy **F10** můžete krokovat s prvním řádkem kódu, který nalezne objekt hry **přehrávače** pomocí značky jako parametru.

8. Když najedete myší ukazatel myši na proměnnou **přehrávače** v okně editoru kódu, zobrazí se její přidružení členové. Můžete dokonce rozšířit překryv a zobrazit podřízené vlastnosti.

    ![okno ladění v editoru Visual Studio pro Mac](media/unity-image31.png)

9. Stiskněte klávesu **F5** nebo stiskněte tlačítko **Spustit** a pokračujte v provádění. Vraťte se do Unity, abyste viděli datovou krychli Enemy opakovaně pro přístup k datové krychli přehrávače. Pokud není vidět, možná budete muset fotoaparát upravit.

    ![přehrávání scény v Unity](media/unity-image32.png)

10. Přepněte zpět na **Visual Studio pro Mac** a nastavte zarážku na prvním řádku **aktualizační** metody. Měl by se hned vysáhnout.

    ![Odebrání zarážky v Visual Studio pro Mac](media/unity-image33.png)

11. Předpokládejme, že je rychlost příliš rychlá a chceme otestovat dopad změny bez restartování aplikace. V okně **Automatické** hodnoty nebo **místní** hodnoty Najděte proměnnou **rychlost** a pak ji změňte na **"10"** a stiskněte klávesu **ENTER**.

    ![Úprava proměnných v okně místních hodnot](media/unity-image34.png)

12. Odeberte zarážku a stisknutím klávesy **F5** pokračujte v provádění.

13. Vraťte se do **Unity** a zobrazte spuštěnou aplikaci. Datová krychle Enemy se teď přesouvá na páté původní rychlosti.

    ![okno Unity se spuštěnou aplikací](media/unity-image35.png)

14. Kliknutím na tlačítko **Přehrát** znovu zastavte aplikaci Unity.

    ![zastavuje se aplikace Unity.](media/unity-image36.png)

15. Vraťte se na **Visual Studio pro Mac**. Kliknutím na tlačítko **zastavit** zastavte relaci ladění.

    ![zastavuje se relace ladění v Visual Studio pro Mac](media/unity-image37.png)

## <a name="task-4-exploring-unity-features-in-visual-studio-for-mac"></a>Úloha 4: zkoumání funkcí Unity v Visual Studio pro Mac

1. Visual Studio pro Mac poskytuje rychlý přístup k dokumentaci Unity v editoru kódu. Umístěte kurzor někam do symbolu **Vector3** v rámci metody **Update** a stiskněte klávesu **⌘ Command + '**.

    ![Výběr metody v aplikaci Visual Studio pro Mac Editor](media/unity-image38.png)

2. Otevře se nové okno prohlížeče v dokumentaci pro **Vector3**. Po splnění tohoto okna zavřete okno prohlížeče.

    ![Otevře se okno prohlížeče s dokumentací](media/unity-image39.png)

3. Visual Studio pro Mac také poskytuje některým pomocníkům k rychlému vytváření tříd chování Unity. Z **Průzkumník řešení** klikněte pravým tlačítkem na **assety** a vyberte **Přidat > nový MonoBehaviour**.

    ![Nová akce kontextu MonoBehaviour](media/unity-image40.png)

4. Nově vytvořená Třída poskytuje zástupné procedury pro metody **Start** a **Update** . Po pravé závorce metody **Update** začněte psát **"-MouseUp"**. Při psaní si všimněte, že technologie IntelliSense v aplikaci Visual Studio je v rámci metody, kterou plánujete implementovat, rychle nulová. Vyberte ji ze seznamu poskytnutých funkcí automatického dokončování. Vyplní pro vás zástupnou proceduru metody, včetně všech parametrů.

    ![IntelliSense v Visual Studio pro Mac](media/unity-image41.png)

5. Uvnitř metody " **MouseUp** " zadejte **"Base".** pro zobrazení všech základních metod, které jsou k dispozici pro volání. Můžete také prozkoumat různá přetížení každé funkce pomocí možnosti stránkování v pravém horním rohu informačního rámečku technologie IntelliSense.

    ![prozkoumávání přetížení v Visual Studio pro Mac](media/unity-image42.png)

6. Visual Studio pro Mac také umožňují snadno definovat nové shadery. Z **Průzkumník řešení** klikněte pravým tlačítkem na **prostředky** a vyberte **Přidat > nový shader**.

    ![Nová akce shaderu v Visual Studio pro Mac](media/unity-image43.png)

7. Formát souboru shaderu získá plnou barvu a zpracování písma, aby bylo snazší ho číst a pochopit.

    ![zvýraznění syntaxe](media/unity-image44.png)

8. Vraťte se do **Unity**. Uvidíte, že protože Visual Studio pro Mac pracuje se stejným systémem projektu, změny provedené na obou místech se automaticky synchronizují s druhým. Teď je snadné použít pro úkol nejlepší nástroj.

    ![panel Asset Unity](media/unity-image45.png)

## <a name="summary"></a>Shrnutí

V tomto testovacím prostředí jste se naučili, jak začít vytvářet hry s Unity a Visual Studio pro Mac. [https://unity3d.com/learn](https://unity3d.com/learn)Další informace o Unity najdete v tématu.
