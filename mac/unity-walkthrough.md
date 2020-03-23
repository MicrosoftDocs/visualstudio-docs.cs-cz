---
title: Začínáme s tvorbou her pomocí platformy Unity
description: Začínáme s Unity a Visual Studio pro Mac
author: heiligerdankgesang
ms.author: dominicn
ms.date: 05/20/2019
ms.technology: vs-ide-general
ms.assetid: D07FA43B-9D18-4DFA-8343-CD538FAD84DB
ms.openlocfilehash: c25df777a9af10859c70741a78c880a57c6f5b8e
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/20/2020
ms.locfileid: "74984791"
---
# <a name="getting-started-building-games-with-unity-in-visual-studio-for-mac"></a>Začínáme vytvářet hry s Unity ve Visual Studiu pro Mac

Unity je herní engine, který vám umožní vyvíjet hry v C#. Tento návod ukazuje, jak začít vyvíjet a ladit unity hry pomocí Visual Studio pro Mac a Visual Studio pro Mac Tools for Unity rozšíření vedle prostředí Unity.

Visual Studio for Mac Tools for Unity je bezplatné rozšíření nainstalované s Visual Studio for Mac. Umožňuje vývojářům Unity využívat funkce pro zvýšení produktivity sady Visual Studio for Mac, včetně vynikající podpory Technologie IntelliSense, funkcí ladění a dalších funkcí.

## <a name="objectives"></a>Cíle

> [!div class="checklist"]
> * Další informace o vývoji Unity pomocí Visual Studia pro Mac

## <a name="prerequisites"></a>Požadavky

- Visual Studio pro[https://www.visualstudio.com/vs/mac](https://www.visualstudio.com/vs/visual-studio-mac)Mac ( )
- Unity 5.6.1 Personal Edition[https://store.unity.com](https://store.unity.com/)nebo vyšší ( , vyžaduje ke spuštění unity.com účet)

## <a name="intended-audience"></a>Zamýšlená cílová skupina

Tato testovací prostředí je určena pro vývojáře, kteří jsou obeznámeni s C#, i když hluboké zkušenosti není vyžadováno.

## <a name="task-1-creating-a-basic-unity-project"></a>Úkol 1: Vytvoření základního projektu Unity

1. Spusťte **Unity**. Pokud o to chcete, přihlaste se.

2. Klepněte na tlačítko **Nový**.

    ![Nové tlačítko v jednotě](media/unity-image1.png)

3. Nastavte **název projektu** na **"UnityLab"** a vyberte **3D**. Klepněte na **tlačítko Vytvořit projekt**.

    ![vytvořit novou obrazovku projektu](media/unity-image2.png)

4. Nyní se díváte na výchozí rozhraní Unity. Má hierarchii scény s herními objekty vlevo, 3D pohled na prázdnou scénu zobrazenou uprostřed, podokno souborů projektu dole a inspektor a služby vpravo. Samozřejmě, je tu mnohem víc, než to, ale to je málo z nejdůležitějších složek.

    ![prázdné rozhraní jednoty](media/unity-image3.png)

5. Pro vývojáře nové Unity, vše, co běží ve vaší aplikaci bude existovat v kontextu **scény**. Soubor scény je jeden soubor, který obsahuje všechny druhy metadat o zdrojích použitých v projektu pro aktuální scénu a její vlastnosti. Když zabalíte aplikaci pro platformu, výsledná aplikace skončí jako kolekce jedné nebo více scén a kódu závislého na platformě, který přidáte. V projektu můžete mít libovolný počet scén.

6. Nová scéna má jen kameru a směrové světlo v něm. Scéna vyžaduje **kameru,** aby bylo vidět cokoli, a **zvukový posluchač,** aby bylo možné cokoli slyšitelné. Tyto součásti jsou připojeny k **GameObject**.

7. Vyberte objekt **Hlavní kamera** z podokna **Hierarchie.**

    ![hlavní objekt fotoaparátu zvýrazněný v podokně hierarchie](media/unity-image4.png)

8. Vyberte podokno **Inspektor** z pravé strany okna a zkontrolujte jeho vlastnosti. Vlastnosti kamery zahrnují informace o transformaci, pozadí, typ projekce, zorné pole a tak dále. Ve výchozím nastavení byla také přidána komponenta Posluchač zvuku, která v podstatě vykresluje zvuk scény z virtuálního mikrofonu připojeného ke kameře.

    ![podokno inspektor](media/unity-image5.png)

9. Vyberte objekt **Směrové světlo.** To poskytuje světlo na scénu tak, aby součásti, jako jsou shaders vědět, jak vykreslit objekty.

    ![směrové světlo objektu zvýrazněné](media/unity-image6.png)

10. Pomocí **inspektoru** můžete zjistit, zda obsahuje běžné vlastnosti osvětlení včetně textu, barvy, intenzity, typu stínu a tak dále.

    ![pohled na vlastnosti v podokně inspektoru](media/unity-image7.png)

11. Je důležité zdůraznit, že projekty v Unity se trochu liší od jejich protějšky Visual Studio pro Mac. Na kartě **Projekt** dole klikněte pravým tlačítkem myši na složku **Datové zdroje** a vyberte Příkaz od Krýt **ve Finderu**.

    ![odhalit v kontextu finder akce](media/unity-image8.png)

12. Projekty obsahují **datové zdroje**, **knihovnu**, **projectsettings**a **dočasné** složky, jak je vidět. Jediný, který se však zobrazí v rozhraní, je složka **Prostředky.** Složka **Knihovna** je místní mezipaměť pro importované datové zdroje. obsahuje všechna metadata pro datové zdroje. Složka **ProjectSettings** ukládá nastavení, která můžete konfigurovat. Složka **Temp** se používá pro dočasné soubory z Mono a Unity během procesu sestavení. K dispozici je také soubor řešení, který můžete otevřít v sadě Visual Studio pro Mac **(UnityLab.sln** zde).

    ![aktiva ve vyhledávači](media/unity-image9.png)

13. Zavřete okno **Finderu** a vraťte se do **Unity**.

14. Složka **Majetek** obsahuje všechny vaše datové zdroje, kód, zvuk atd. Teď je prázdný, ale každý soubor, který do svého projektu vnesete, jde sem. Toto je vždy složka nejvyšší úrovně v **Editoru jednoty**. Ale vždy přidávejte a odebírat soubory prostřednictvím rozhraní Unity (nebo Visual Studio pro Mac) a nikdy přímo prostřednictvím systému souborů.

    ![složka datových zdrojů v jednotě](media/unity-image10.png)

15. **GameObject** je ústředním bodem vývoje v Unity jako téměř vše, co pochází z tohoto typu, včetně modelů, světla, částicové systémy, a tak dále. Přidejte do scény nový objekt **Krychle** prostřednictvím nabídky **GameObject > 3D objekt > krychle.**

    ![objekt datové krychle ve scéně](media/unity-image11.png)

16. Podívejte se rychle na vlastnosti nového **GameObject** a uvidíte, že má název, značku, vrstvu a transformaci. Tyto vlastnosti jsou společné pro všechny **GameObjects**. Kromě toho bylo k **krychli** připojeno několik součástí, které poskytují potřebné funkce, včetně síťového filtru, urychlovače rámečku a rendereru.

    ![vlastnosti herního objektu](media/unity-image12.png)

17. Přejmenujte objekt **Krychle,** který má ve výchozím nastavení název **"Kostka",** na **"Nepřítel"**. Změnu uložte stisknutím **klávesy Enter.** To bude nepřítel kostka v naší jednoduché hře.

    ![vlastnost objektu datové krychle](media/unity-image13.png)

18. Přidejte další **objekt Cube** do scény stejným postupem jako výše a pojmenujte tento **"Player"**.

    ![přejmenování druhého objektu datové krychle](media/unity-image14.png)

19. Označte také objekt přehrávače **"Přehrávač"** (viz rozevírací ovládací **prvek Tag** přímo pod polem názvu). Použijeme to v nepřátelském skriptu, abychom pomohli najít herní objekt hráče.

    ![označení objektu přehrávače](media/unity-image15.png)

20. V zobrazení **Scéna** přesuňte objekt přehrávače mimo nepřátelský objekt podél osy Z pomocí myši. Podél osy Z se můžete pohybovat tak, že vyberete a přetáhnete krychli po **jejím červeném** panelu směrem k **modré** čáře. Vzhledem k tomu, že kostka žije ve 3D prostoru, ale může být přetažena pouze ve 2D pokaždé, osa, na kterou přetáhnete, je obzvláště důležitá.

    ![zobrazení scény zobrazující krychli](media/unity-image16.png)

21. Posuňte kostku dolů a doprava podél osy. Tím se aktualizuje **vlastnost Transform.Position** v **inspektoru**. Nezapomeňte přetáhnout na místo podobně jako zde uvedené, abyste usnadnili pozdější kroky v testovacím prostředí.

    ![přesunutí jedné krychle podél osy](media/unity-image17.png)

22. Nyní můžete přidat nějaký kód řídit nepřítele logiku tak, aby sleduje hráče. Klepněte pravým tlačítkem myši na složku **Datové zdroje** na panelu **Projekt** a vyberte příkaz Vytvořit > **skript c#**.

    ![Akce kontextu skriptu jazyka C#](media/unity-image18.png)

23. Pojmenujte nový skript Jazyka **C# "EnemyAI"**.

    ![Skript jazyka C#](media/unity-image19.png)

24. Chcete-li připojit skripty k herním objektům, přetáhněte nově vytvořený skript na objekt **Enemy** v podokně **Hierarchie.** Nyní tento objekt bude používat chování z tohoto skriptu.

    ![zvýraznění znázorňující přidání skriptu do herního objektu](media/unity-image20.png)

25. Vyberte **Soubor > Uložit scény,** chcete-li uložit aktuální scénu. **Pojmenujte ji "MyScene"**.

## <a name="task-2-working-with-visual-studio-for-mac-tools-for-unity"></a>Úkol 2: Práce s Visual Studio pro Mac Nástroje pro jednotu

1. Nejlepší způsob, jak upravit kód C#, je použít Visual Studio pro Mac. Unity můžete nakonfigurovat tak, aby používala Visual Studio pro Mac jako výchozí obslužnou rutinu. Vyberte **Předvolby Unity >**.

2. Vyberte kartu **Externí nástroje.** V rozevíracím seznamu **Externí editor skriptů** vyberte **Procházet** a vyberte **Aplikace/Visual Studio.app**. Případně pokud už existuje možnost **Visual Studia,** vyberte ji.

    ![karta externí nástroje v předvolbách](media/unity-image21.png)

3. Unity je teď nakonfigurovaná tak, aby **používala Visual Studio for Mac** pro úpravy skriptů. Zavřete dialogové okno **Předvolby jednoty.**

    ![Visual Studio vybrané v předvolbách](media/unity-image22.png)

4. Poklepáním **EnemyAI.cs** otevřete v **Visual Studiu for Mac**.

    ![Nepřátelský majetek vybraný v jednotě](media/unity-image23.png)

5. Řešení sady Visual Studio je jednoduché. Obsahuje složku **Datové zdroje** (stejnou z **Finderu)** a **EnemyAI.cs** skript vytvořený dříve. V sofistikovanějších projektech bude hierarchie pravděpodobně vypadat jinak než to, co vidíte v Unity.

    ![Panel řešení ve Visual Studiu pro Mac](media/unity-image24.png)

6. **EnemyAI.cs** je otevřena v editoru. Počáteční skript obsahuje pouze zástupné procedury pro metody **Start** a **Update.**

7. Nahraďte počáteční nepřátelský kód níženým kódem.

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

8. Podívejte se rychle na jednoduché chování nepřítele, které je zde definováno. V **Metodě Start** získáme odkaz na objekt přehrávače (jeho značkou) a také jeho **transformaci**. V **metodě Update,** která se nazývá každý snímek, se nepřítel přesune směrem k objektu hráče. Klíčová slova a názvy používají barevné kódování, aby bylo snazší pochopit základ kódu v Sadě Visual Studio pro Mac.

9. Uložte změny nepřátelského skriptu ve **Visual Studiu for Mac**.

## <a name="task-3-debugging-the-unity-project"></a>Úkol 3: Ladění projektu Unity

1. Nastavte zarážku na prvním řádku kódu v metodě **Start.** Můžete buď kliknout na okraj editoru na cílové čáře, nebo umístit kurzor na řádek a stisknout **klávesu F9**.

    ![nastavení zarážky ve Visual Studiu pro Mac](media/unity-image25.png)

2. Klepněte na tlačítko **Spustit ladění** nebo stiskněte **klávesu F5**. To bude sestavení projektu a připojit jej k Unity pro ladění.

    ![tlačítko start ve visual studiu pro Mac](media/unity-image26.png)

3. Vraťte se do **Unity** a kliknutím na tlačítko **Spustit** spusťte hru.

    ![spustit tlačítko v jednotě](media/unity-image27.png)

4. Zarážka by měla být přístupů a nyní můžete použít Visual Studio pro Mac ladění nástroje.

    ![zásah zarážky ve visual studiu pro Mac](media/unity-image28.png)

5. Z **locals** pad, vyhledejte **tento** ukazatel, který odkazuje na **Objekt EnemyAI.** Rozbalte odkaz a uvidíte, že můžete procházet přidružené členy, jako **je Rychlost**.

    ![místní ladění pad ve visual studiu pro Mac](media/unity-image29.png)

6. Odeberte zarážku z metody **Start** stejným způsobem, jakým byla přidána - buď klepnutím na okraj nebo výběrem řádku a stisknutím **klávesy F9**.

    ![zásah zarážky ve visual studiu pro Mac](media/unity-image30.png)

7. Stisknutím **klávesy F10** překroužete první řádek kódu, který najde herní objekt **přehrávače** pomocí značky jako parametru.

8. Najeďte kurzorem myši na proměnnou **přehrávače** v okně editoru kódu a zobrazte jeho přidružené členy. Můžete dokonce rozbalit překrytí a zobrazit podřízené vlastnosti.

    ![okno ladění ve visual studiu pro mac editor](media/unity-image31.png)

9. Stisknutím **klávesy F5** nebo stisknutím tlačítka **Spustit** pokračujte v provádění. Návrat do jednoty vidět nepřítele kostka opakovaně blíží hráč kostka. Pokud fotoaparát není viditelný, může být nutné fotoaparát upravit.

    ![scéna hraje v jednotě](media/unity-image32.png)

10. Přepněte zpět do **Visual Studia for Mac** a nastavte zarážku na prvním řádku metody **Update.** Mělo by to být zasaženo okamžitě.

    ![nastavení zarážky ve Visual Studiu pro Mac](media/unity-image33.png)

11. Předpokládejme, že rychlost je příliš rychlá a chceme otestovat dopad změny bez restartování aplikace. Vyhledejte proměnnou **Rychlost** v okně **Autos** nebo **Locals,** změňte ji na **"10"** a stiskněte **Enter**.

    ![úprava proměnných v místním okně](media/unity-image34.png)

12. Odeberte zarážku a stisknutím **klávesy F5** pokračujte v provádění.

13. Vraťte se do **unity** zobrazit spuštěnou aplikaci. Nepřátelská kostka se nyní pohybuje pětinou původní rychlosti.

    ![okno jednoty se spuštěnou aplikací](media/unity-image35.png)

14. Zastavte aplikaci Unity opětovným kliknutím na tlačítko **Přehrát.**

    ![zastavení aplikace unity](media/unity-image36.png)

15. Vraťte se do **Visual Studia pro Mac**. Zastavte relaci ladění klepnutím na tlačítko **Zastavit.**

    ![zastavení relace ladění v sadě Visual Studio for Mac](media/unity-image37.png)

## <a name="task-4-exploring-unity-features-in-visual-studio-for-mac"></a>Úkol 4: Zkoumání funkcí Unity ve Visual Studiu pro Mac

1. Visual Studio pro Mac poskytuje rychlý přístup k dokumentaci Unity v editoru kódu. Umístěte kurzor někde na symbol **Vektor3** v rámci metody **Update** a stiskněte **tlačítko # Command + '**.

    ![výběr metody ve Visual Studiu pro mac editor](media/unity-image38.png)

2. Otevře se nové okno prohlížeče v dokumentaci k **Vector3**. Zavřete okno prohlížeče, pokud je spokojen.

    ![otevře se okno prohlížeče v dokumentaci](media/unity-image39.png)

3. Visual Studio for Mac také poskytuje některé pomocníky pro rychlé vytvoření tříd chování Unity. V **Průzkumníku řešení**klepněte pravým tlačítkem myši na **položku Prostředky** a vyberte přidat > nové **monochování**.

    ![nová kontextová akce monochování](media/unity-image40.png)

4. Nově vytvořená třída poskytuje zástupné procedury pro metody **Start** a **Update.** Po uzavření složená závorka **Update** metoda, začněte psát **"onmouseup"**. Při psaní si všimněte, že technologie IntelliSense sady Visual Studio se rychle zaměřuje na metodu, kterou plánujete implementovat. Vyberte ji z poskytnutého seznamu automatického dokončování. Vyplní pro vás proceduru, včetně všech parametrů.

    ![intellisense ve visual studiu pro Mac](media/unity-image41.png)

5. Uvnitř metody **OnMouseUp** zadejte **"base".** zobrazíte všechny základní metody, které jsou k dispozici pro volání. Můžete také prozkoumat různá přetížení jednotlivých funkcí pomocí možnosti stránkování v pravém horním rohu informačního rámečku IntelliSense.

    ![zkoumání přetížení ve visual studiu pro Mac](media/unity-image42.png)

6. Visual Studio pro Mac také umožňuje snadno definovat nové shadery. V **Průzkumníku řešení**klepněte pravým tlačítkem myši na **položku Datové zdroje** a vyberte přidat > nový **shader**.

    ![nová akce shaderu ve visual studiu pro Mac](media/unity-image43.png)

7. Formát souboru shader dostane plnou barvu a zpracování písma, aby bylo snazší číst a pochopit.

    ![zvýraznění syntaxe](media/unity-image44.png)

8. Návrat k **jednotě**. Uvidíte, že vzhledem k tomu, že Visual Studio pro Mac pracuje se stejným systémem projektu, změny provedené na obou místech jsou automaticky synchronizovány s ostatními. Nyní je snadné vždy použít nejlepší nástroj pro daný úkol.

    ![panel unity asset](media/unity-image45.png)

## <a name="summary"></a>Souhrn

V této laboratoři jste se naučili, jak začít vytvářet hru s Unity a Visual Studio pro Mac. Podívejte [https://unity3d.com/learn](https://unity3d.com/learn) se na další informace o Jednotě.
