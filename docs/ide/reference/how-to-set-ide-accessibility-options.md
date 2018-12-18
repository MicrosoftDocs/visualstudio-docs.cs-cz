---
title: 'Postupy: nastavení možností usnadnění přístupu v integrovaném vývojovém prostředí'
description: Zjistěte, jak nastavení možností usnadnění přístupu v sadě Visual Studio, které vám usnadní jeho integrované vývojové prostředí (IDE) pro každodenní použití, včetně uživatelů, kteří mají ke čtení a pro uživatele, kteří mají omezenou pohyblivostí k zápisu.
ms.date: 08/22/2017
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- accessibility [Visual Studio]
ms.assetid: ddc96c4c-0600-46c1-8267-7dce4c44ad24
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: df94a57358edd9619b43bbcddb26d4e3485a1ab1
ms.sourcegitcommit: dd839de3aa24ed7cd69f676293648c6c59c6560a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/27/2018
ms.locfileid: "52388423"
---
# <a name="how-to-set-ide-accessibility-options"></a>Postupy: nastavení možností usnadnění přístupu v integrovaném vývojovém prostředí

> [!TIP]
> Další informace o nedávných aktualizacích usnadnění přístupu, najdete v článku [vylepšení přístupnosti v sadě Visual Studio 2017 verze 15.3](https://blogs.msdn.microsoft.com/visualstudio/2017/08/14/accessibility-improvements-in-visual-studio-2017-version-15-3/) blogový příspěvek.

[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] obsahuje funkce, které usnadňují pro uživatele, kteří mají ke čtení a pro uživatele, kteří mají omezenou pohyblivostí k zápisu. Tyto funkce patří změna velikost a barvu textu v editorech, změna velikosti textu a tlačítka na panely nástrojů a automatické dokončování pro parametry, metody a další.

Kromě toho [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] podporuje typech klávesnic, které nejčastěji zadávané znaky přístupnější. Můžete také přizpůsobit výchozí klávesové zkratky, který je k dispozici [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Další informace najdete v tématu [určení a přizpůsobení klávesových zkratek](../../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md).

> [!NOTE]
> Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici. Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky. Další informace najdete v tématu [Resetovat nastavení](../environment-settings.md#reset-settings).

## <a name="editors-dialogs-and-tool-windows"></a>Editory, dialogová okna a okna nástrojů

 Ve výchozím nastavení, dialogová okna a okna nástrojů v [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] použít stejnou velikost písma a barvy jako operační systém. Nastavení barev pro rámce IDE, dialogová okna, panely nástrojů a okna nástrojů jsou založeny barevném schématu: světlý nebo tmavý. Můžete změnit aktuální barvu motivu v [Obecné, prostředí, dialogové okno Možnosti](../../ide/reference/general-environment-options-dialog-box.md).

 Automaticky otevíraná okna můžete také zobrazit v zobrazení kódu z editoru. Tato okna můžete vyzvat vás Dostupní členové na aktuální objekt a parametry pro dokončení funkce nebo příkaz. Tato okna, může být užitečné, pokud máte potíže s psaním. Ale narušují fokus v editoru kódu, který může být problematické pro některé uživatele. Můžete vypnout tato okna tak, že otevřete dialogové okno Možnosti a vymazání **automatický seznam členů** a **informace o parametrech** v **textový Editor**, **všechny Jazyky**, **Obecné** stránku **možnosti** dialogové okno.

 Můžete změnit uspořádání oken v integrovaném vývojovém prostředí (IDE) aby co nejlépe vyhovovalo způsob, jakým pracujete. Můžete ukotvit, float, skrýt nebo automaticky skrýt každé okno nástroje.

 Další informace o tom, jak změnit rozložení oken, naleznete v tématu [přizpůsobení rozložení oken](../../ide/customizing-window-layouts-in-visual-studio.md).

### <a name="changing-the-size-of-text"></a>Změna velikosti textu

 Můžete změnit nastavení pro textový panel nástrojů, jako například **příkaz** okně **okamžité** okně a **výstup** okno v **písma a Barvy** podokně **prostředí** možnosti **nástroje** dialogové okno. Když **[všechny textový nástroj Windows]** výběru v **zobrazit nastavení pro** rozevíracího seznamu ve výchozím nastavení je uveden jako **výchozí** v **popředí položky**  a **položky pozadí** rozevírací seznamy. Můžete také změnit nastavení pro zobrazení textu v editoru.

#### <a name="to-change-the-size-of-text-in-text-based-tool-windows-and-editors"></a>Chcete-li změnit velikost textu v oknech nástroje pracujícího s textem a editory

1.  Z **nástroje** nabídce zvolte **možnosti**.

2.  Zvolte **písma a barvy** na **prostředí** složky.

3.  Vyberte možnost na **zobrazit nastavení pro** rozevírací nabídky.

     Chcete-li změnit velikost písma textu v editoru, zvolte **textový Editor**.

     Chcete-li změnit velikost písma pro text v oknech nástroje pracujícího s textem, zvolte **[všechny textový nástroj Windows]**.

     Chcete-li změnit velikost písma pro text popisu tlačítka v editoru, zvolte **Nápověda editoru**.

     Chcete-li změnit velikost písma textu v příkazu dokončení automaticky otevíraná okna, zvolte **dokončování**.

4.  Z **zobrazení položek**vyberte **prostý Text**.

5.  V **písmo**, vyberte nový typ písma.

6.  V **velikost**, vyberte novou velikost písma.

    > [!NOTE]
    > Chcete-li obnovit velikost okna textových nástrojů a editory, zvolte **použít výchozí hodnoty**.

7.  Zvolte **OK**.

### <a name="change-the-colors-that-are-used-in-the-ide"></a>Změna barvy, které se používají v prostředí IDE

 Můžete také změnit výchozí barvy pro text, okraj ukazatele, prázdné znaky a prvky kódu v editoru.

> [!NOTE]
> Chcete-li použít vysoký kontrast – barvy pro všechny aplikace pro windows v operačním systému, stiskněte vlevo <strong>ALT +</strong>vlevo **SHIFT + PRINT SCREEN**. Pokud [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] je otevřete, zavřete a znovu otevřít [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] plně implementovat vysoký kontrast – barvy.

#### <a name="to-change-the-color-of-items-in-the-editor"></a>Chcete-li změnit barva položek v editoru

1.  Z **nástroje** nabídce zvolte **možnosti**.

2.  V **prostředí** složky, zvolte **písma a barvy**.

3.  V **zobrazit nastavení pro**, zvolte **textový Editor**.

4.  Z **zobrazení položek**, vyberte nějakou položku, jejichž zobrazení je potřeba změnit, jako například **prostý Text**, **okraj indikátoru**, **viditelné prázdné znaky**, **Atributu HTML Name**, nebo **atribut XML**.

5.  Vyberte zobrazení nastavení z následujících možností: **popředí položky**, **položky pozadí**, a **tučné**.

6.  Zvolte **OK**.

## <a name="toolbars"></a>Panely nástrojů

 Vylepšení nástrojů použitelnost a přístupnost, přidáním textu tlačítka na panelu nástrojů.

### <a name="to-assign-text-to-toolbar-buttons"></a>Přiřadit text tlačítka na panelu nástrojů

1.  Z **nástroje** nabídce zvolte **vlastní**.

2.  V **vlastní** dialogové okno, vyberte **příkazy** kartu.

3.  Vyberte **nástrojů** a pak zvolte možnost, která obsahuje tlačítko, které chcete zobrazit text pro název panelu nástrojů.

4.  V seznamu vyberte příkaz, který máte v úmyslu změnit.

5.  Zvolte **změnit výběr**.

6.  Zvolte **obrázků a textu**.

### <a name="to-modify-the-displayed-text-in-a-button"></a>Chcete-li změnit zobrazený text tlačítku

1.  Znovu vyberte **změnit výběr**.

2.  V blízkosti **název**, vložit zadejte nový popisek vybraného tlačítka.

## <a name="see-also"></a>Viz také:

* [Funkce pro usnadnění přístupu sady Visual Studio](../../ide/reference/accessibility-features-of-visual-studio.md)
* [Prostředky pro navržení aplikací usnadňujících přístup](../../ide/reference/resources-for-designing-accessible-applications.md)