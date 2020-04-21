---
title: Použití nástrojů sady Visual Studio pro jednotu | Dokumenty společnosti Microsoft
ms.custom: ''
ms.date: 07/03/2018
ms.technology: vs-unity-tools
ms.topic: conceptual
ms.assetid: e67ec9a2-a449-413e-8930-9a471bd43a06
author: therealjohn
ms.author: johmil
manager: crdun
ms.workload:
- unity
ms.openlocfilehash: d1bca9bed18de822de71ca441387adeaefc65ec3
ms.sourcegitcommit: ade07bd1cf69b8b494d171ae648cfdd54f7800d3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/21/2020
ms.locfileid: "81649400"
---
# <a name="use-visual-studio-tools-for-unity"></a>Používání Visual Studio Tools for Unity

V této části se dozvíte, jak používat nástroje Visual Studio pro funkce integrace a produktivity Unity a jak používat ladicí program Visual Studio pro vývoj Unity.

## <a name="open-unity-scripts-in-visual-studio"></a>Otevření skriptů Unity v sadě Visual Studio

Jakmile visual studio je [nastavenjako externí editor skriptů pro unity](getting-started-with-visual-studio-tools-for-unity.md#configure-unity-for-use-with-visual-studio), otevření libovolného skriptu z editoru Unity se automaticky spustí nebo přepnout do Visual Studio s vybraným skriptem otevřené. Stačí dvakrát kliknout na skript v projektu Unity.

Případně můžete otevřít Visual Studio bez skriptu otevřeného ve zdrojovém editoru výběrem **open c# projektu** z nabídky **Datové zdroje** v unity.

![Otevřít projekt Jazyka C#](media/vstu_open-csharp-project.png)

## <a name="unity-documentation-access"></a>Přístup k dokumentaci Unity

Můžete rychle přistupovat k dokumentaci skriptování Unity z Visual Studia. Pokud Visual Studio Tools for Unity nenajde dokumentaci rozhraní API místně, pokusí se ji najít online.

- V sadě Visual Studio zvýrazněte nebo umístěte kurzor nad rozhraní Unity API, o kterém se chcete dozvědět, a pak stiskněte **kombinaci kláves Ctrl**+**Alt**+**M**, **Ctrl**+**H**

## <a name="intellisense-for-unity-api-messages"></a>Intellisense pro zprávy unity API

Dokončování kódu Intellisense usnadňuje implementaci zpráv Unity API ve skriptech MonoBehaviour a pomáhá s učením rozhraní Unity API. Použití zpráv IntelliSense for Unity:

1. Umístěte kurzor na nový řádek uvnitř těla třídy, která je odvozena od `MonoBehaviour`.

2. Začněte psát název zprávy Unity, `OnTriggerEnter`například .

3. Po napsání písmen "**ontri**" se zobrazí seznam návrhů IntelliSense.

   ![Používání atributu IntelliSense](media/vstu_intellisense1.png)

4. Výběr v seznamu lze změnit třemi způsoby:

    - Pomocí kláves se šipkami **nahoru** a **dolů.**

    - Kliknutím myší na požadovanou položku.

    - Dalším zadáním názvu požadované položky.

5. Technologie IntelliSense může vložit vybranou zprávu Unity, včetně všech nezbytných parametrů:

    - Stisknutím **klávesy Tab**.

    - Stisknutím **klávesy Enter**.

    - Poklepáním na vybranou položku.

   ![Vložit zprávu Unity ze služby IntelliSense](media/vstu_intellisense2.png)

## <a name="unity-monobehavior-scripting-wizard"></a>Průvodce skriptováním Unity MonoBehavior

Průvodce MonoBehavior můžete použít k zobrazení seznamu všech metod rozhraní UNITY API a rychlé implementaci prázdné definice. Tato funkce, zejména s **možnost generovat metodu komentáře** povolena, je užitečné, pokud jste stále učení, co je k dispozici v rozhraní API Unity.

Chcete-li vytvořit prázdné definice metod MonoBehavior pomocí průvodce MonoBehavior:

1. V sadě Visual Studio umístěte kurzor na místo, kam chcete vložit metody, a stisknutím **klávesctrl**+**shift**+**M** spusťte Průvodce monochováním.

2. V okně **Vytvořit metody skriptu** zaškrtněte políčko vedle názvu každé metody, kterou chcete přidat.

3. Pomocí rozevíracího souboru **Verze rozhraní** vyberte požadovanou verzi.

4. Ve výchozím nastavení jsou metody vloženy na pozici kurzoru. Případně můžete zvolit jejich vložení po libovolné metodě, která je již implementována ve vaší třídě změnou hodnoty rozevíracího **souboru kurzoru** na požadované umístění.

5. Pokud chcete, aby průvodce generoval komentáře pro vybrané metody, zaškrtněte políčko **Generovat komentáře metody.** Tyto komentáře jsou určeny k tomu, aby vám pomohly pochopit, kdy je metoda volána a jaké jsou její obecné povinnosti.

6. Zvolte tlačítko **OK,** chcete-li průvodce ukončit a vložit metody do kódu.

   ![Dialogové okno průvodce monochováním.](../cross-platform/media/vstu_monobehavior_wizard_full.png "vstu_monobehavior_wizard_full")

## <a name="unity-project-explorer"></a>Průzkumník projektu Unity

![Okno Průzkumníka projektu Unity.](../cross-platform/media/vstu_unity_project_explorer.png "vstu_unity_project_explorer")

Unity Project Explorer zobrazuje všechny soubory projektu Unity a adresáře stejným způsobem, jako unity editor. To je jiný než navigace unity skripty s normální Visual Studio Průzkumník řešení, který je organizuje do projektů a řešení generované Visual Studio.

- V hlavní nabídce Sady Visual Studio zvolte **Zobrazit > Průzkumníka projektů Unity**. Klávesová zkratka: **Alt**+**Shift**+**E**

   ![Zobrazení okna Průzkumníka projektu Unity.](../cross-platform/media/vstu_view_unity_project_explorer.png "vstu_view_unity_project_explorer")

## <a name="unity-debugging"></a>Ladění jednoty

Visual Studio Tools for Unity umožňuje ladit editor a herní skripty pro váš projekt Unity pomocí výkonného ladicího programu visual studia.

### <a name="debug-in-the-unity-editor"></a>Ladění v editoru Unity

#### <a name="start-debugging"></a>Zahájit ladění

1. Připojte visual studio k jednotě klepnutím na tlačítko **Přehrát** označené **připojit k jednotě**nebo pomocí klávesové zkratky **F5**.

   ![Klikněte na Přehrát v Sadě Visual Studio.](media/vstu_play-button.png)

2. Přepněte na Unity a kliknutím na tlačítko **Přehrát** spusťte hru v editoru.

   ![Klikněte na Přehrát v jednotě](media/vstu_unity-play-button.png)

3. Když hra běží v editoru Unity při připojení k Visual Studio, všechny zarážky zjištěné pozastaví provádění hry a zobrazí řádek kódu, kde hra narazí na zarážku v sadě Visual Studio.

#### <a name="stop-debugging"></a>Zastavit ladění

- Klepněte na tlačítko **Zastavit** v sadě Visual Studio nebo použijte klávesovou zkratku **Shift + F5**.

  ![Klikněte na Zastavit v sadě Visual Studio.](media/vstu_stop-debugger.png)

Další informace o ladění v sadě Visual Studio najdete v [tématu První pohled na ladicí program sady Visual Studio](../debugger/debugger-feature-tour.md).

#### <a name="attach-to-unity-and-play"></a>Připojte se k jednotě a přehrávání

Pro větší pohodlí můžete změnit **tlačítko Připojit k jednotě** připojit **k režimu Unity a Play.**

1. Klikněte na malou **šipku dolů** vedle tlačítka **Připojit k jednotě.**

1. V rozevírací nabídce vyberte **Připojit k jednotě a přehrát.**

    ![Připojení a přehrávání](media/vstu_attach-and-play.png)

Tlačítko přehrávání se stane označeno **připojit k jednotě a přehrát**. Kliknutím na toto tlačítko nebo pomocí klávesové zkratky **F5** se nyní automaticky přepne do editoru Unity a spustí hru v editoru, kromě připojení ladicího programu Sady Visual Studio.

Kliknutím na tlačítko **Zastavit** v sadě Visual Studio nebo pomocí klávesové zkratky **Shift**+**F5** automaticky zastavíte hru v editoru Unity.

### <a name="debug-unity-player-builds"></a>Ladění Unity hráč staví

Můžete ladit vývoj sestavení různých unity přehrávače s Visual Studio.

#### <a name="enable-script-debugging-in-a-unity-player"></a>Povolení ladění skriptů v přehrávači Unity

1. V unity otevřete nastavení sestavení výběrem **souboru > nastavení sestavení**.

2. V okně Nastavení sestavení označte zaškrtávací políčka **Ladění vývojového sestavení** a **skriptů.**

   ![Nakonfigurujte nastavení sestavení Unity pro ladění.](../cross-platform/media/vstu_debugging_build_settings.png "vstu_debugging_build_settings")

#### <a name="select-a-unity-instance-to-attach-the-debugger-to"></a>Vyberte instanci Unity, ke které chcete připojit ladicí program.

- V sadě Visual Studio v hlavní nabídce zvolte **Ladění > připojit ladicí program jednoty**.

   ![Připojte ladicí program Unity.](../cross-platform/media/vstu_debugging_attach_unity_debugger.png "vstu_debugging_attach_unity_debugger")

   Dialogové okno **Vybrat jednotu instance** zobrazí některé informace o každé instanci Unity, ke které se můžete připojit.

   ![Zvolte instanci Unity, ke které se chcete připojit.](../cross-platform/media/vstu_attach-debugger.png "vstu_connection_to_unity")

   **Project**

   Název projektu Unity, který je spuštěn v této instanci Unity.

   **Stroj** Název počítače nebo zařízení, na kterých je spuštěna tato instance Unity.

   **Editor typů,** **Editor** pokud je tato instance Unity spuštěna jako součást Editoru jednoty; **Přehrávač,** pokud je tato instance Unity samostatným hráčem.

   **Přístav** Číslo portu soketu UDP, přes který tato instance Unity komunikuje.

> [!IMPORTANT]
> Vzhledem k tomu, že Visual Studio Tools for Unity a instance Unity komunikují přes síťový soket UDP, může se na to vás zeptat brána firewall. Pokud k tomu dojde, budete muset autorizovat připojení tak, aby VSTU a Unity můžete komunikovat.

### <a name="debug-a-dll-in-your-unity-project"></a>Ladění dll v projektu Unity

Mnoho vývojářů Unity píše součásti kódu jako externí knihovny DLL, takže funkce, které vyvíjejí, lze snadno sdílet s jinými projekty. Visual Studio Tools for Unity usnadňuje ladění kódu v těchto knihovnách DLL bez problémů s jiným kódem v projektu Unity.

> [!NOTE]
> V tuto chvíli Visual Studio Tools for Unity podporuje pouze spravované knihovny DLL. Nepodporuje ladění nativních kódů DLL, jako jsou například napsané v jazyce C++.

Všimněte si, že scénář popsaný zde předpokládá, že máte zdrojový kód – to znamená, že vyvíjíte nebo znovu používáte vlastní kód první strany, nebo máte zdrojový kód do knihovny třetí strany a plánujete jeho nasazení v projektu Unity jako knihovnu DLL. Tento scénář nepopisuje ladění dll, pro které nemáte zdrojový kód.

#### <a name="to-debug-a-managed-dll-project-used-in-your-unity-project"></a>Ladění spravovaného projektu DLL použitého v projektu Unity

1. Přidejte existující projekt DLL do řešení Visual Studio generovaného nástroji Visual Studio Tools for Unity. Méně často se může spouštět nový spravovaný projekt DLL, který obsahuje součásti kódu v projektu Unity; Pokud tomu tak je, můžete přidat nový spravovaný projekt Knihovny DLL do řešení sady Visual Studio. Další informace o přidání nového nebo existujícího projektu do řešení naleznete v tématu [How to: Add Projects to a Solution](https://msdn.microsoft.com/library/ff460187.aspx).

   ![Přidejte existující projekt DLL do řešení.](../cross-platform/media/vstu_debugging_dll_add_existing.png "vstu_debugging_dll_add_existing")

   V obou případech Visual Studio Tools for Unity udržuje odkaz na projekt, i v případě, že má znovu obnovit soubory projektu a řešení, takže stačí provést tyto kroky jednou.

2. Odkaz na správný profil architektury Unity v projektu DLL. V sadě Visual Studio ve vlastnostech projektu DLL nastavte vlastnost **Framework target** na verzi architektury Unity, kterou používáte. Toto je unity základní třídy knihovny, která odpovídá kompatibilitě rozhraní API, které váš projekt cíle, jako je například Unity úplné, mikro nebo webové základní třídy knihovny. Tím zabráníte vaší dll volání metod rozhraní, které existují v jiných architekturách nebo úrovně kompatibility, ale které nemusí existovat v rozhraní Unity verze, kterou používáte.

> [!NOTE]
> Následující je vyžadováno pouze v případě, že používáte starší runtime Unity. Pokud používáte nový modul runtime Unity, už nemusíte používat tyto vyhrazené profily 3.5. Použijte profil .NET 4.x kompatibilní s verzí Unity.

   ![Nastavte cílovou architekturu dll na unity framework.](../cross-platform/media/vstu_debugging_dll_target_framework.png "vstu_debugging_dll_target_framework")

3. Zkopírujte knihovnu DLL do složky Asset projektu Unity. V Unity jsou datové zdroje soubory, které jsou zabaleny a nasazeny společně s vaší aplikací Unity, aby je bylo možné načíst za běhu. Vzhledem k tomu, že knihovny DLL jsou propojeny za běhu, musí být knihovny DLL nasazeny jako prostředky. Chcete-li být nasazenjako prostředek, Unity Editor vyžaduje Knihovny DLL, které mají být umístěny uvnitř složky Prostředky v projektu Unity. To lze provést dvěma způsoby:

   - Upravte nastavení sestavení projektu DLL tak, aby zahrnovala úlohu po sestavení, která kopíruje výstupní soubory DLL a PDB z výstupní složky do složky **Datové zdroje** projektu Unity.

   - Upravte nastavení sestavení projektu DLL a nastavte jeho výstupní složku tak, aby byla složky **Datové zdroje** projektu Unity. Soubory DLL i PDB budou umístěny do složky **Datové zdroje.**

   Soubory PDB jsou potřebné pro ladění, protože obsahují ladicí symboly dll a mapovat kód DLL do formuláře zdrojového kódu. Pokud cílíte na starší runtime, Visual Studio Tools for Unity použije informace z DLL a PDB k vytvoření dll. MDB, což je formát ladicí symbol používaný starším skriptovacím strojem Unity. Pokud cílíte na nový runtime a pomocí portable-PDB, Visual Studio Tools for Unity se nebude snažit provést žádný převod symbolu jako nový runtime Unity je schopen nativně využívat přenosné pdbs.

   Více informací o generaci PDB naleznete [zde](../debugger/how-to-set-debug-and-release-configurations.md). Pokud cílíte na nový runtime, ujistěte se, že "Ladění informace" je nastavena na "Portable", aby bylo možné správně generovat Portable-PDB. Pokud cílíte na starší runtime, musíte použít "Full".

4. Ladění kódu. Nyní můžete ladit zdrojový kód DLL společně se zdrojovým kódem projektu Unity a použít všechny funkce ladění, na které jste zvyklí, jako jsou zarážky a krokování kódu.

## <a name="keyboard-shortcuts"></a>Klávesové zkratky

Můžete rychle přistupovat k nástrojům Unity pro visual studio funkce pomocí jejich klávesové zkratky. Zde je přehled zkratek, které jsou k dispozici.

|Příkaz|Zástupce|Název příkazu zástupce|
|-------------|--------------|---------------------------|
|Otevření Průvodce monochováním|**Ctrl**+**Shift**+**M**|**EditorContextMenus.CodeWindow.ImplementMonoBehaviours**|
|Otevření Průzkumníka projektu Unity|**Alt**+**Shift**+**E**|**Aplikace View.UnityProjectExplorer**|
|Přístup k dokumentaci Unity|**Ctrl**+**Alt**+**M, Ctrl**+**H**|**Help.UnityAPIReference**|
|Připojit k ladicímu programu Unity (přehrávač nebo editor)|**_žádné výchozí nastavení_**|**Ladicí program:AttachUnityDebugger**|

Pokud se vám nelíbí výchozí nastavení, můžete změnit kombinace klávesových zkratek. Informace o tom, jak ji změnit, najdete [v tématu Identifikace a přizpůsobení klávesových zkratek v sadě Visual Studio](../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md).
