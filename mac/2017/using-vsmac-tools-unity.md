---
title: Použití Visual Studia pro Mac Nástroje pro jednotu
description: Tato příručka popisuje použití rozšíření Visual Studio for Mac Tools for Unity
author: therealjohn
ms.author: johmil
ms.date: 07/17/2017
ms.assetid: 83FDD7A3-5D16-4B4B-9080-078E3FB5C623
ms.openlocfilehash: d4df59273db1fab8492b36e87e48e0e770072f17
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/20/2020
ms.locfileid: "79303293"
---
# <a name="using-visual-studio-for-mac-tools-for-unity"></a>Použití Visual Studia pro Mac Nástroje pro jednotu

V této části se dozvíte, jak používat Visual Studio pro Mac Nástroje pro unity integrace a produktivity funkce a jak používat Visual Studio pro Mac ladicí program pro vývoj Unity.

## <a name="opening-unity-scripts-in-visual-studio-for-mac"></a>Otevření skriptů Unity ve Visual Studiu pro Mac

Jakmile je Visual Studio for Mac [nastavenjako externí editor skriptů pro Unity](setup-vsmac-tools-unity.md#configure-unity-for-use-with-visual-studio-for-mac), otevření libovolného skriptu z editoru Unity se automaticky spustí nebo přepne na Visual Studio for Mac s otevřeným zvoleným skriptem.

Případně Visual Studio pro Mac lze otevřít bez skriptu otevřít ve zdrojovém editoru výběrem **Open C# Project** z nabídky **Prostředky** v Unity.

![Otevřít projekt Jazyka C#](media/using-vsmac-tools-unity-image1.png)

## <a name="unity-documentation-access"></a>Přístup k dokumentaci Unity

Visual Studio for Mac Tools for Unity obsahuje zástupce pro přístup k dokumentaci rozhraní UNITY API. Chcete-li získat přístup k dokumentaci rozhraní Unity API z Visual Studia for Mac, umístěte kurzor nad rozhraní UNITY API, o kterém se chcete dozvědět, a stiskněte **příkaz 啦 + "**.

## <a name="intellisense-for-unity-messages"></a>Zprávy IntelliSense for Unity
Unity engine vysílá zprávy do skriptů MonoBehaviour, což umožňuje vývojářům psát kód, který reaguje na zprávy, jako je OnMouseDown, OnTriggerEnter, atd. Protože se nejedná o virtuální metody v základní monobehavior třídy, některé IDE, jako je Například MonoDevelop chybí funkce dokončení kódu pro zprávy Unity.

Visual Studio for Mac Tools for Unity však rozšiřuje své funkce IntelliSense na zprávy Unity. To usnadňuje implementaci unity zprávy ve skriptech MonoBehaviour a pomáhá s učením Unity API. Použití zpráv IntelliSense for Unity:

1. Umístěte kurzor na nový řádek uvnitř těla třídy, která je odvozena od MonoBehaviour.

2. Začněte psát název zprávy Unity, `OnTriggerEnter`například .

3. Po zadání písmen "**ont**" se zobrazí seznam návrhů Technologie IntelliSense.

   ![Používání atributu IntelliSense](media/using-vsmac-tools-unity-image2.png)

4. Výběr v seznamu lze změnit třemi způsoby:

   * Pomocí kláves se šipkami **nahoru** a **dolů.**

   * Kliknutím myší na požadovanou položku.

   * Dalším zadáním názvu požadované položky.

5. Technologie IntelliSense může vložit vybranou zprávu Unity, včetně všech nezbytných parametrů:

   * Stisknutím **klávesy Tab**.

   * Stisknutím **klávesy Return**.

   * Poklepáním na vybranou položku.

   ![Vložit zprávu Unity ze služby IntelliSense](media/using-vsmac-tools-unity-image3.png)

## <a name="adding-new-unity-files-and-folders"></a>Přidání nových souborů a složek Unity

Zatímco můžete vždy přidat nové soubory do projektu Unity v editoru Unity, Visual Studio pro Mac umožňuje snadno vytvářet nové skripty Unity, shadery a složky z visual studia.

### <a name="add-a-new-c-monobehaviour-script"></a>Přidání nového skriptu C# MonoBehaviour

Chcete-li přidat nový skript C# MonoBehaviour, **klepněte pravým tlačítkem myši na složku Prostředky** nebo na jeden z jejích podadresářů v panelu Řešení a vyberte přidat > nové **monochování**.

![Přidat nové MonoBehaviour](media/using-vsmac-tools-unity-image4.png)

### <a name="add-a-new-unity-shader"></a>Přidání nového shaderu Unity

Chcete-li přidat nový shader Unity, **klepněte pravým tlačítkem myši na složku Datové zdroje** nebo na podadresář v panelu Řešení a vyberte přidat > nový **shader**.

### <a name="add-a-new-folder"></a>Přidání nové složky

Chcete-li přidat novou složku, **klepněte pravým tlačítkem myši na složku Datové zdroje** nebo podadresář na panelu Řešení a vyberte příkaz Přidat > novou **složku**.

Tyto dodatky se projeví v okně Projektu editorunity.

### <a name="to-rename-a-file-or-folder"></a>Přejmenování souboru nebo složky
**Klikněte pravým tlačítkem myši** na položku, kterou chcete přejmenovat na panelu Řešení, a vyberte **přejmenovat...**.

> [!NOTE]
> Pokud máte nový projekt Unity bez skriptů a složka Prostředky se nezobrazí v panelu Řešení v sadě Visual Studio for Mac, přidejte počáteční skript Jazyka C# z editoru Unity.

## <a name="unity-debugging"></a>Ladění jednoty

Unity projekty lze ladit pomocí Visual Studio pro Mac.

### <a name="start-debugging"></a>Zahájit ladění

Zahájení ladění:

1. Připojte Visual Studio k jednotě klepnutím na tlačítko **Přehrát** nebo zadáním **příkazu + returnu**nebo **f5**.

   ![Klikněte na Přehrát v Sadě Visual Studio.](media/using-vsmac-tools-unity-image5.png)

2. Přepněte na Unity a kliknutím na tlačítko **Přehrát** spusťte hru v editoru.

   ![Klikněte na Přehrát v jednotě](media/using-vsmac-tools-unity-image6.png)

3. Když hra běží v editoru Unity při připojení k Visual Studio, všechny zarážky zjištěné pozastaví provádění hry a zobrazí řádek kódu, kde hra narazí na zarážku v sadě Visual Studio for Mac.

### <a name="stop-debugging"></a>Zastavit ladění

Ukončení ladění:

1. Klepněte na tlačítko **Zastavit** v Sadě Visual Studio pro Mac nebo stiskněte **Shift + Command + Return**.

   ![Klikněte na Zastavit v sadě Visual Studio.](media/using-vsmac-tools-unity-image7.png)

Další informace o ladění v Visual Studiu pro Mac najdete v [tématu Použití ladicího programu](debugging.md).
