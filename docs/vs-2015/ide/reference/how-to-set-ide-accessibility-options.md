---
title: 'Postupy: nastavení možností usnadnění přístupu k IDE | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- accessibility [Visual Studio]
ms.assetid: ddc96c4c-0600-46c1-8267-7dce4c44ad24
caps.latest.revision: 25
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: afff9e06c4333f4910e22e963d24090c1d1e4c6a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72651336"
---
# <a name="how-to-set-ide-accessibility-options"></a>Postupy: nastavení možnosti usnadnění přístupu IDE
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] obsahuje funkce, které usnadňují čtení a pro lidi, kteří mají omezená pohyblivost k zápisu, pro lidi, kteří mají slabý zrak. Mezi tyto funkce patří změna velikosti a barvy textu v editorech, změna velikosti textu a tlačítek na panelech nástrojů a automatické dokončování pro metody a parametry, pro pojmenování několika.

 Kromě toho [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] podporuje rozložení klávesnice Dvorak, které usnadňují přístup k často zadaným znakům. Můžete také přizpůsobit výchozí klávesové zkratky, které jsou k dispozici v nástroji [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] . Další informace najdete v tématu [identifikace a přizpůsobení klávesových zkratek](../../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md).

> [!NOTE]
> Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici. Chcete-li změnit nastavení, v nabídce **nástroje** klikněte na položku **Nastavení importu a exportu** . Další informace naleznete v tématu [přizpůsobení nastavení vývoje v aplikaci Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).

## <a name="editors-dialogs-and-tool-windows"></a>Editory, dialogová okna a okna nástrojů
 Ve výchozím nastavení používají dialogová okna a okna nástrojů [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] stejnou velikost písma a barvy jako operační systém. Nastavení barev pro rámeček rozhraní IDE, dialogová okna, panely nástrojů a okna nástrojů jsou založena na barevném schématu: světlá nebo tmavá. Aktuální barevný motiv můžete změnit v [dialogovém okně Obecné, prostředí, možnosti](../../ide/reference/general-environment-options-dialog-box.md).

 Můžete také zobrazit automaticky otevíraná okna v zobrazení kódu editoru. Tato okna vás mohou vyzvat s dostupnými členy na aktuálním objektu a parametry k dokončení funkce nebo příkazu. Tato okna můžou být užitečná, pokud máte potíže při psaní. Nicméně narušují fokus v editoru kódu, což může být pro některé uživatele problematické. Tato okna můžete vypnout otevřením dialogového okna Možnosti a vymazáním informací o **členech** a **parametrech** automatického seznamu v **textovém editoru**, na stránce **všechny jazyky**, **Obecné** v dialogovém okně **Možnosti** . Další informace naleznete v tématu [How to: set a General Editor Options](https://msdn.microsoft.com/704e4a7b-2162-4bed-8a47-f4f6ffec98c2).

 Můžete změnit uspořádání oken v integrovaném vývojovém prostředí (IDE) tak, aby nejlépe vyhovovala způsobu, jakým pracujete. Jednotlivá okna nástroje můžete ukotvit, floatovat, skrývat nebo automaticky skrývat.

 Další informace o tom, jak změnit rozložení oken, najdete v tématu [přizpůsobení rozložení oken](../../ide/customizing-window-layouts-in-visual-studio.md).

### <a name="changing-the-size-of-text"></a>Změna velikosti textu
 V podokně **písma a barvy** v možnostech **prostředí** v dialogovém okně **nástroje** můžete změnit nastavení textových oken založených na textu, jako je okno **příkazového** řádku, okno **okamžité** a **výstup** . Pokud je vybrána možnost **[všechna okna textových nástrojů]** v rozevíracím seznamu **Zobrazit nastavení pro** rozevírací seznam, výchozí nastavení je uvedeno jako **výchozí** v rozevíracích seznamech **položky** a **pozadí položky** . Můžete také změnit nastavení způsobu zobrazení textu v editoru.

##### <a name="to-change-the-size-of-text-in-text-based-tool-windows-and-editors"></a>Změna velikosti textu v textových oknech a editorech nástrojů

1. V nabídce **nástroje** klikněte na příkaz **Možnosti**.

2. Vyberte **písma a barvy** ve složce **prostředí** .

3. Vyberte možnost v rozevírací nabídce **Zobrazit nastavení pro** .

     Chcete-li změnit velikost písma textu v editoru, vyberte možnost **textový editor**.

     Chcete-li změnit velikost písma textu v textových oknech nástrojů, vyberte možnost **[všechna okna textových nástrojů]**.

     Chcete-li změnit velikost písma textu popisku v editoru, klikněte na tlačítko **Editor popis**.

     Chcete-li změnit velikost písma textu v místních oknech dokončování příkazů, vyberte možnost **dokončování příkazů**.

4. V **zobrazení položky**vyberte **prostý text**.

5. V **písma**vyberte nový typ písma.

6. V rámečku **Velikost**vyberte novou velikost písma.

    > [!NOTE]
    > Chcete-li obnovit velikost textu textových oken a editorů založených na textu, vyberte možnost **použít výchozí**.

7. Vyberte **OK**.

### <a name="changing-the-colors-used-in-the-ide"></a>Změna barev použitých v integrovaném vývojovém prostředí
 Můžete také zvolit, že chcete změnit výchozí barvy pro text, indikátory okrajů, prázdné znaky a prvky kódu v editoru.

> [!NOTE]
> Chcete-li pro všechna okna aplikací v operačním systému použít barvy s vysokým kontrastem, stiskněte levé tlačítko <strong>ALT +</strong>levý **SHIFT + PRINT SCREEN**. Pokud [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] je otevřená, zavřete a znovu otevřete, [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] abyste plně implementovali barvy s vysokým kontrastem.

##### <a name="to-change-the-color-of-items-in-the-editor"></a>Změna barvy položek v editoru

1. V nabídce **nástroje** klikněte na příkaz **Možnosti**.

2. Vyberte **písma a barvy** ze složky **prostředí** .

3. V **zobrazení zobrazit nastavení pro**vyberte **textový editor**.

4. V položce **Zobrazit položky**vyberte položku, jejíž zobrazení potřebujete změnit, například **prostý text**, **okraj indikátoru**, **viditelné prázdné znaky**, **název atributu HTML**nebo **atribut XML**.

5. Vyberte nastavení zobrazení z následujících možností: **popředí položky**, **pozadí položky**a **tučné**.

6. Vyberte **OK**.

## <a name="toolbars"></a>Panely nástrojů
 Pro zlepšení použitelnosti panelu nástrojů a usnadnění přístupu můžete přidat text na tlačítka panelu nástrojů.

#### <a name="to-assign-text-to-toolbar-buttons"></a>Přiřazení textu k tlačítkům panelu nástrojů

1. V nabídce **nástroje** vyberte možnost **přizpůsobit**.

2. V dialogovém okně **přizpůsobit** vyberte kartu **příkazy** .

3. Vyberte **panel nástrojů** a potom zvolte název panelu nástrojů, který obsahuje tlačítko, pro které chcete zobrazit text.

4. V seznamu vyberte příkaz, který máte v úmyslu změnit.

5. Vyberte možnost **změnit výběr**.

6. Vyberte **obrázek a text**.

#### <a name="to-modify-the-buttons-displayed-text"></a>Úprava zobrazeného textu tlačítka

1. Znovu vyberte **změnit výběr**.

2. Vedle pole **název**zadejte pro vybrané tlačítko Nový titulek.

## <a name="see-also"></a>Viz také
 [Funkce usnadnění](../../ide/reference/accessibility-features-of-visual-studio.md) [pro navrhování přístupných aplikací v prostředcích](../../ide/reference/resources-for-designing-accessible-applications.md) sady Visual Studio
