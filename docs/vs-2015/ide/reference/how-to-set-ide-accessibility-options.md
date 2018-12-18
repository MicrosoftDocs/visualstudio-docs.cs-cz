---
title: 'Postupy: nastavení možností usnadnění přístupu IDE | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- accessibility [Visual Studio]
ms.assetid: ddc96c4c-0600-46c1-8267-7dce4c44ad24
caps.latest.revision: 25
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 485529a8be2adf57f7b79a3d2f0844d662920448
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49867283"
---
# <a name="how-to-set-ide-accessibility-options"></a>Postupy: nastavení možnosti usnadnění přístupu IDE
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] obsahuje funkce, které usnadňují pro uživatele, kteří mají ke čtení a pro uživatele, kteří mají omezenou pohyblivostí k zápisu. Tyto funkce patří změna velikost a barvu textu v editorech, změna velikosti textu a tlačítka na panely nástrojů a automatické dokončování pro parametry, metody a další.  
  
 Kromě toho [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] podporuje typech klávesnic, které nejčastěji zadávané znaky přístupnější. Můžete také přizpůsobit výchozí klávesové zkratky, který je k dispozici [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]. Další informace najdete v tématu [určení a přizpůsobení klávesových zkratek](../../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md).  
  
> [!NOTE]
>  Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici. Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky. Další informace najdete v tématu [přizpůsobení nastavení pro vývoj v sadě Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## <a name="editors-dialogs-and-tool-windows"></a>Editorech, dialogových oken a nástroj pro Windows  
 Ve výchozím nastavení, dialogová okna a okna nástrojů v [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] použít stejnou velikost písma a barvy jako operační systém. Nastavení barev pro rámce IDE, dialogová okna, panely nástrojů a okna nástrojů jsou založeny barevném schématu: světlý nebo tmavý. Můžete změnit aktuální barvu motivu v [Obecné, prostředí, dialogové okno Možnosti](../../ide/reference/general-environment-options-dialog-box.md).  
  
 Automaticky otevíraná okna můžete také zobrazit v zobrazení kódu z editoru. Tato okna můžete vyzvat vás Dostupní členové na aktuální objekt a parametry pro dokončení funkce nebo příkaz. Tato okna, může být užitečné, pokud máte potíže s psaním. Ale narušují fokus v editoru kódu, který může být problematické pro některé uživatele. Můžete vypnout tato okna tak, že otevřete dialogové okno Možnosti a vymazání **automatický seznam členů** a **informace o parametrech** v **textový Editor**, **všechny Jazyky**, **Obecné** stránku **možnosti** dialogové okno. Další informace najdete v tématu [postupy: nastavení možností editoru Obecné](http://msdn.microsoft.com/en-us/704e4a7b-2162-4bed-8a47-f4f6ffec98c2).  
  
 Můžete změnit uspořádání oken v integrovaném vývojovém prostředí (IDE) aby co nejlépe vyhovovalo způsob, jakým pracujete. Můžete ukotvit, float, skrýt nebo automaticky skrýt každé okno nástroje.  
  
 Další informace o tom, jak změnit rozložení oken, naleznete v tématu [přizpůsobení rozložení oken](../../ide/customizing-window-layouts-in-visual-studio.md).  
  
### <a name="changing-the-size-of-text"></a>Změna velikosti textu  
 Můžete změnit nastavení pro textový panel nástrojů, jako například **příkaz** okně **okamžité** okně a **výstup** okno v **písma a Barvy** podokně **prostředí** možnosti **nástroje** dialogové okno. Když **[všechny textový nástroj Windows]** výběru v **zobrazit nastavení pro** rozevíracího seznamu ve výchozím nastavení je uveden jako **výchozí** v **popředí položky**  a **položky pozadí** rozevírací seznamy. Můžete také změnit nastavení pro zobrazení textu v editoru.  
  
##### <a name="to-change-the-size-of-text-in-text-based-tool-windows-and-editors"></a>Chcete-li změnit velikost textu v oknech nástroje pracujícího s textem a editory  
  
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
    >  Chcete-li obnovit velikost okna textových nástrojů a editory, zvolte **použít výchozí hodnoty**.  
  
7.  Zvolte **OK**.  
  
### <a name="changing-the-colors-used-in-the-ide"></a>Změna barvy použité v integrovaném vývojovém prostředí  
 Můžete také změnit výchozí barvy pro text, okraj ukazatele, prázdné znaky a prvky kódu v editoru.  
  
> [!NOTE]
>  Chcete-li použít vysoký kontrast – barvy pro všechny aplikace pro windows v operačním systému, stiskněte vlevo <strong>ALT +</strong>vlevo **SHIFT + PRINT SCREEN**. Pokud [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] je otevřete, zavřete a znovu otevřít [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] plně implementovat vysoký kontrast – barvy.  
  
##### <a name="to-change-the-color-of-items-in-the-editor"></a>Chcete-li změnit barva položek v editoru  
  
1.  Z **nástroje** nabídce zvolte **možnosti**.  
  
2.  Zvolte **písma a barvy** z **prostředí** složky.  
  
3.  V **zobrazit nastavení pro**, zvolte **textový Editor**.  
  
4.  Z **zobrazení položek**, vyberte nějakou položku, jejichž zobrazení je potřeba změnit, jako například **prostý Text**, **okraj indikátoru**, **viditelné prázdné znaky**, **Atributu HTML Name**, nebo **atribut XML**.  
  
5.  Vyberte zobrazení nastavení z následujících možností: **popředí položky**, **položky pozadí**, a **tučné**.  
  
6.  Zvolte **OK**.  
  
## <a name="toolbars"></a>Panely nástrojů  
 Vylepšení nástrojů použitelnost a přístupnost, přidáním textu tlačítka na panelu nástrojů.  
  
#### <a name="to-assign-text-to-toolbar-buttons"></a>Přiřadit text tlačítka na panelu nástrojů  
  
1.  Z **nástroje** nabídce zvolte **vlastní**.  
  
2.  V **vlastní** dialogové okno, vyberte **příkazy** kartu.  
  
3.  Vyberte **nástrojů** a pak zvolte možnost, která obsahuje tlačítko, které chcete zobrazit text pro název panelu nástrojů.  
  
4.  V seznamu vyberte příkaz, který máte v úmyslu změnit.  
  
5.  Zvolte **změnit výběr**.  
  
6.  Zvolte **obrázků a textu**.  
  
#### <a name="to-modify-the-buttons-displayed-text"></a>Chcete-li na tlačítko změnit zobrazený text  
  
1.  Znovu vyberte **změnit výběr**.  
  
2.  V blízkosti **název**, vložit zadejte nový popisek vybraného tlačítka.  
  
## <a name="see-also"></a>Viz také  
 [Funkce pro usnadnění přístupu sady Visual Studio](../../ide/reference/accessibility-features-of-visual-studio.md)   
 [Zdroje pro navrhování aplikací usnadňujících přístup](../../ide/reference/resources-for-designing-accessible-applications.md)



