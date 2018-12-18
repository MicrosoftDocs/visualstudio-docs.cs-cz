---
title: Propojení prvků modelu a pracovních položek | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.teamarch.common.removeworkitemsdialog
- vs.teamarch.common.linkworkitemsdialog
helpviewer_keywords:
- UML - extending, linking to TFS work items
- UML - extending, linking work items
- work items, creating from UML models
- UML model, creating work items
- work items, linking to UML models
- UML model, linking work items
ms.assetid: e687a490-0f93-412c-a1ff-eea83cf7ba07
caps.latest.revision: 49
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 55dfd83f3c9324b08bbb88c8404350c2aebf129f
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51752072"
---
# <a name="link-model-elements-and-work-items"></a>Propojení prvků modelu a pracovních položek
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sledujte úkoly, testovací případy, chyby, požadavky, problémy a další práci související s modelem propojením prvků modelu v sadě Visual Studio a pracovní položky v Team Foundation Server nebo Visual Studio Team Services. Připojte dokumenty k propojeným pracovním položkám, které chcete přidružit prvkům modelu.  
  
 Tuto funkci podporovat kterou verzí sady Visual Studio najdete v tématu [podporované verze pro nástroje architektury a modelování](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  
  
> [!NOTE]
>  K vytváření a otvírání odkazů je nutné použít Průzkumník týmových projektů. Přesvědčte se, zda jsou vaše diagramy a projekt modelování zapsány do správy verzí, aby ostatní uživatelé mohli otevírat propojené diagramy.  
  
 Propojit můžete například:  
  
- Pracovní položku uživatelského scénáře a diagram aktivity, chcete-li zobrazit, jak vytvořit scénář jako posloupnost operací  
  
- Případ použití v diagramu případu a pracovní položky testovacího případu, chcete-li se ujistit, že je případ použití implementován správně  
  
- Atribut ve třídě v diagramu tříd UML a pracovní položku chyby, chcete-li zobrazit chybu v implementaci atributu  
  
- Komponentu v diagramu komponent a pracovní položku úkolu, chcete-li sledovat vývoj komponenty. Taková úloha je obvykle rozdělena na menší úlohy  
  
  Pracovní položky je možné spojit s libovolným prvkem, který lze vybrat v diagramech modelování nebo v Průzkumníku modelů UML, jako tyto položky:  
  
- Všechny prvky v modelech UML, jako jsou například třídy UML, životní dráhy, případy použití, podsystémy, aktivity, uzly objektů, komponenty, rozhraní  
  
- Všechny vztahy v modelech UML, jako jsou například asociace, generalizace, závislosti, toky, zprávy  
  
- Části prvků, jako jsou například atributy a operace tříd, výskyty spuštění životních drah, vstupní a výstupní spojky aktivit a části a porty komponent  
  
- Vrstvy a závislosti vrstev  
  
- Komentáře a odkazy komentářů  
  
- Diagramy. Chcete-li zvolit diagram, vyberte prázdnou část diagramu.  
  
> [!WARNING]
>  Musíte už být připojení k TFS zdrojového kódu ovládacího prvku (SCC) vytvořit nebo propojit s pracovní položkou. Pokud se pokusíte otevřít připojení k jiné SCC TFS, Visual Studio automaticky zavře aktuální řešení. Ujistěte se, že jste již připojeni k příslušné SCC než se pokusíte vytvořit nebo propojit s pracovní položkou. V pozdějších verzích sady Visual Studio příkazy nabídky nejsou k dispozici v případě, že nejste připojeni k SCC.  
  
-   [Připojení k týmovému projektu](#ConnectTFS)  
  
-   [Propojení prvku modelu s novou pracovní položkou](#LinkNew)  
  
-   [Propojení prvku modelu s existující pracovní položkou](#LinkExisting)  
  
-   [Zobrazit pracovní položky propojeny s prvkem modelu](#OpenWorkItem)  
  
-   [Zobrazení prvků modelu propojených s pracovní položkou](#ViewLinkedModels)  
  
-   [Odstranění propojení mezi elementy modelu a pracovních položek](#RemoveLinks)  
  
-   [Odstraňování potíží](#Troubleshooting)  
  
##  <a name="ConnectTFS"></a> Připojení k týmovému projektu  
 Nejprve musíte připojit k vašemu týmovému projektu k vytvoření, zobrazení nebo odebrání odkazů.  
  
1.  Na **týmu** nabídce zvolte **spravovat připojení** zobrazíte okno Průzkumníku týmových projektů.  
  
2.  Pokud se nezobrazí správný projekt v Průzkumníku týmových projektů zvolte **spravovat připojení** a klikněte na tlačítko **připojit k týmovému projektu**. Následně vyberte správné projekty, v případě potřeby také server.  
  
3.  V **Team Exploreru**, vyberte projekt, ve kterém chcete vytvořit, propojit nebo zobrazit pracovní položky.  
  
##  <a name="LinkNew"></a> Propojení prvku modelu s novou pracovní položkou  
  
1.  Ujistěte se, že jste připojení k instanci TFS, který chcete použít.  
  
2.  V diagramu modelování nebo v **Průzkumníku modelů UML**, otevřete místní nabídku pro ovládací prvek modelu.  
  
3.  Zvolte **vytvořit pracovní položku** a typů pracovních položek, které chcete vytvořit.  
  
4.  Vyplňte pole pracovní položky. Zvolte **uložit pracovní položku**.  
  
     Systém Visual Studio propojí prvek modelu s novou pracovní položkou. Zobrazí se ikona na prvku modelu nebo blízko něj.  
  
> [!WARNING]
>  Musíte už být připojení k TFS zdrojového kódu ovládacího prvku (SCC) vytvořit nebo propojit s pracovní položkou. Pokud se pokusíte otevřít připojení k jiné SCC TFS, Visual Studio automaticky zavře aktuální řešení. Ujistěte se, že jste již připojeni k příslušné SCC než se pokusíte vytvořit nebo propojit s pracovní položkou. V pozdějších verzích sady Visual Studio příkazy nabídky nejsou k dispozici v případě, že nejste připojeni k SCC.  
  
##  <a name="LinkExisting"></a> Propojení prvku modelu s existující pracovní položkou  
 Při propojování prvků modelu s pracovními položkami začněte z prvku modelu, nikoli z pracovní položky.  
  
1.  Ujistěte se, že jste připojení k instanci TFS, který chcete použít.  
  
2.  V diagramu modelování nebo v **Průzkumníku modelů UML**, otevřete místní nabídku pro ovládací prvek modelu. Zvolte **propojit s pracovní položkou**. Vyberte projekt v **projektu** pole.  
  
3.  Zvolte jednu nebo více pracovních položek pro propojení s prvkem modelu pomocí jednoho z těchto kroků:  
  
    -   Vyberte dotaz v **uložený dotaz**.  
  
    -   Zadejte identifikátory jedné nebo více pracovních položek oddělené mezerami, v **ID**.  
  
    -   Zadáním slova nebo fráze do pole **název obsahuje**.  
  
4.  Zvolte **najít**.  
  
5.  V seznamu pracovních položek vyberte pracovní položku nebo pracovní položky, které chcete propojit.  
  
     Jakmile budete hotovi, **pracovních položek** vlastnosti prvku modelu bude zobrazovat větší číslo než dříve. Rovněž se zobrazí ikona na prvku modelu nebo blízko něj.  
  
> [!WARNING]
>  Musíte už být připojení k TFS zdrojového kódu ovládacího prvku (SCC) vytvořit nebo propojit s pracovní položkou. Pokud se pokusíte otevřít připojení k jiné SCC TFS, Visual Studio automaticky zavře aktuální řešení. Ujistěte se, že jste již připojeni k příslušné SCC než se pokusíte vytvořit nebo propojit s pracovní položkou. V pozdějších verzích sady Visual Studio příkazy nabídky nejsou k dispozici v případě, že nejste připojeni k SCC.  
  
##  <a name="OpenWorkItem"></a> Zobrazit pracovní položky propojeny s prvkem modelu  
  
1.  V **Team Exploreru**, ujistěte se, že jste připojeni k týmovému projektu ve kterém jsou pracovní položky propojeny s prvkem modelu.  
  
2.  V diagramu modelování nebo v **Průzkumníku modelů UML**, otevřete místní nabídku pro ovládací prvek modelu. Zvolte **zobrazit pracovní položky** k zobrazení seznamu propojených pracovních položek.  
  
    > [!NOTE]
    >  Zobrazí se pouze pracovní položky z aktuálně připojeného serveru. Pokud se nezobrazí žádné pracovní položky, ujistěte se, že jste připojeni ke správnému serveru v **Team Exploreru**.  
  
##  <a name="ViewLinkedModels"></a> Zobrazení prvků modelu propojených s pracovní položkou  
 Můžete zobrazit diagramy modelování a prvky, které jsou propojeny s pracovní položkou v sadě Visual Studio Team Services a Team Foundation Server 2012 nebo novější. Pracovní položky mohou být například spojený s modely tříd, jež zobrazují návrh nových tříd, které budou implementovány.  
  
1.  V **Team Exploreru**, ujistěte se, že jste připojeni k týmovému projektu kde jsou prvky modelu propojeny s pracovní položkou.  
  
    > [!NOTE]
    >  K prohlížení propojených prvků modelu lze použít pouze Průzkumník týmových projektů, nikoli nástroj Team Web Access. Zkontrolujte, zda je váš pracovní prostor mapován na projekt modelování, který obsahuje prvky nebo diagramy modelování. Pokud nemáte pracovní prostor, je třeba jej vytvořit. Zobrazit [Poradce při potížích s](#Troubleshooting) a [vytváření a práci s pracovními prostory](http://msdn.microsoft.com/library/1d7f6ed8-ec7c-48f8-86da-9aea55a90d5a).  
  
2.  Otevřít pracovní položku, zvolte **odkazy**. V části **odkaz modelu**, otevřete místní nabídku pro propojený prvek modelu. Zvolte **otevřít odkazovanou položku**.  
  
     ![Otevřít propojený prvek modelu z pracovní položky](../modeling/media/workitem-openlinkedmodelelement.png "WorkItem_OpenLinkedModelElement")  
  
##  <a name="RemoveLinks"></a> Odstranění propojení mezi elementy modelu a pracovních položek  
 Odeberte propojené pracovní položky, přičemž začněte od prvku modelu. Tato operace z pracovní položky odebere vzájemné propojení s daným prvkem modelu. Pokud byste začali s pracovní položkou, k odstranění vzájemných propojení mezi prvkem modelu a pracovní položkou nedojde.  
  
1.  V diagramu modelování nebo v **Průzkumníku modelů UML**, otevřete místní nabídku pro ovládací prvek modelu.  
  
2.  Zvolte **odebrání pracovních položek**.  
  
     \- nebo –  
  
    1.  Zvolte **vlastnosti**, pak **pracovní položky** kde se zobrazí počet propojených pracovních položek.  
  
    2.  V **pracovních položek** vlastnost, zvolte tlačítko se třemi tečkami **[...]** .  
  
        > [!NOTE]
        >  Zobrazí se pouze pracovní položky na aktuálním serveru. Pokud je seznam prázdný, ale počet pracovních položek není nulový, ujistěte se, že jste připojeni ke správnému serveru v **Team Exploreru**.  
  
3.  V části **odebrat odkazy na pracovní položky**, vymažte vybrané položky, které chcete odpojit. Zvolte **OK**.  
  
##  <a name="Troubleshooting"></a> Řešení potíží  
  
|**Problém**|**Možná příčina**|**Řešení**|  
|---------------|------------------------|--------------------|  
|Nelze najít prvek modelu, který chcete propojit.|Element může být v diagramu v projektu modelování, který je v [!INCLUDE[esprscc](../includes/esprscc-md.md)]. Pravděpodobně nemáte pracovní prostor, který se mapuje na diagram.|Namapujte pracovní prostor na projekt modelování a diagram. Pokud nemáte pracovní prostor, pak je třeba jej vytvořit.<br /><br /> Chybová zpráva, která se pro tuto chybu objeví, obsahuje cestu, kterou lze namapovat na pracovní prostor.<br /><br /> Zobrazit [vytváření a práci s pracovními prostory](http://msdn.microsoft.com/library/1d7f6ed8-ec7c-48f8-86da-9aea55a90d5a).|  
|Nelze nalézt propojený prvek modelu.|Propojený prvek může být na diagramu, který byl přesunut, přejmenován nebo odstraněn.|1.  V pracovní položce odstraňte odkaz na prvek modelu.<br />2.  Vytvořte nové propojení z pracovní položky na prvek modelu.|  
|Pracovní položka nemá očekávané propojené prvky modelu.|Pracovní položka ukazuje propojený prvek vrstvy, pouze pokud bylo propojení vytvořeno z pracovní položky. Pokud váš tým nepoužívá [!INCLUDE[esprscc](../includes/esprscc-md.md)], místní cesta diagramů se použije pro vytvoření propojení. Pokud jsou projekt modelování a jeho diagramy v [!INCLUDE[esprscc](../includes/esprscc-md.md)], všichni členové týmu, kteří mají přístup k projektu, vidět propojené prvky v pracovních položkách.|Zkuste aktualizovat pracovní položku.|  
|Odstraněním propojení k prvku modelu z pracovní položky neodstraníte propojení prvku modelu s pracovní položkou.||Odstraňte odkaz na pracovní položku, přičemž začněte od prvku modelu.|  
  
## <a name="see-also"></a>Viz také  
 [Úpravy modelů a diagramů UML](../modeling/edit-uml-models-and-diagrams.md)   
 [Vytváření modelů pro aplikaci](../modeling/create-models-for-your-app.md)



