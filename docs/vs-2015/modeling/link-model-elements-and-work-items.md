---
title: Propojení prvků modelu a pracovních položek | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: ee4fea9e3fb1d5b4d27b1d520ac2ab036747f73d
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72657634"
---
# <a name="link-model-elements-and-work-items"></a>Propojení prvků modelu a pracovních položek
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Můžete sledovat úkoly, testovací případy, chyby, požadavky, problémy a další práci související s vaším modelem propojením prvků modelu v aplikaci Visual Studio a pracovních položek v Team Foundation Server nebo Visual Studio Team Services. Připojte dokumenty k propojeným pracovním položkám, které chcete přidružit prvkům modelu.

 Chcete-li zjistit, které verze aplikace Visual Studio tuto funkci podporují, přečtěte si téma [podpora verzí pro nástroje pro architekturu a modelování](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

> [!NOTE]
> K vytváření a otevírání odkazů je nutné použít Team Explorer. Přesvědčte se, zda jsou vaše diagramy a projekt modelování zapsány do správy verzí, aby ostatní uživatelé mohli otevírat propojené diagramy.

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
> Aby bylo možné vytvořit nebo propojit pracovní položku, musíte být již připojeni ke správě zdrojového kódu TFS (SCC). Pokud se pokusíte otevřít připojení k jinému SCC TFS, Visual Studio automaticky zavře aktuální řešení. Před pokusem o vytvoření nebo propojení pracovní položky se ujistěte, že jste již připojeni k odpovídajícímu SCC. V novějších verzích sady Visual Studio nejsou příkazy nabídky k dispozici, pokud nejste připojeni k SCC.

- [Připojení k týmovému projektu](#ConnectTFS)

- [Propojení prvku modelu s novou pracovní položkou](#LinkNew)

- [Propojení prvku modelu s existující pracovní položkou](#LinkExisting)

- [Zobrazení pracovních položek propojených s prvkem modelu](#OpenWorkItem)

- [Zobrazení elementů modelu propojených s pracovní položkou](#ViewLinkedModels)

- [Odstranit propojení mezi prvky modelu a pracovními položkami](#RemoveLinks)

- [Odstraňování potíží](#Troubleshooting)

## <a name="ConnectTFS"></a>Připojení k týmovému projektu
 Aby bylo možné vytvořit, zobrazit nebo odebrat odkazy, musíte se nejdřív připojit k vašemu týmovému projektu.

1. V nabídce **tým** vyberte **Spravovat připojení** , aby se zobrazilo okno Team Explorer.

2. Pokud se nezobrazí správný projekt, v Team Explorer zvolte možnost **Spravovat připojení** a pak zvolte **připojit k týmovému projektu**. Následně vyberte správné projekty, v případě potřeby také server.

3. V **Team Explorer**vyberte projekt, ve kterém chcete vytvořit, propojit nebo zobrazit pracovní položky.

## <a name="LinkNew"></a>Propojení prvku modelu s novou pracovní položkou

1. Ujistěte se, že jste připojeni k instanci serveru TFS, kterou chcete použít.

2. V diagramu modelování nebo v **Průzkumníku modelů UML**otevřete místní nabídku pro prvek modelu.

3. Vyberte možnost **vytvořit pracovní položku** a typ pracovní položky, kterou chcete vytvořit.

4. Vyplňte pole pracovní položky. Vyberte **Uložit pracovní položku**.

     Systém Visual Studio propojí prvek modelu s novou pracovní položkou. Zobrazí se ikona na prvku modelu nebo blízko něj.

> [!WARNING]
> Aby bylo možné vytvořit nebo propojit pracovní položku, musíte být již připojeni ke správě zdrojového kódu TFS (SCC). Pokud se pokusíte otevřít připojení k jinému SCC TFS, Visual Studio automaticky zavře aktuální řešení. Před pokusem o vytvoření nebo propojení pracovní položky se ujistěte, že jste již připojeni k odpovídajícímu SCC. V novějších verzích sady Visual Studio nejsou příkazy nabídky k dispozici, pokud nejste připojeni k SCC.

## <a name="LinkExisting"></a>Propojení prvku modelu s existující pracovní položkou
 Při propojování prvků modelu s pracovními položkami začněte z prvku modelu, nikoli z pracovní položky.

1. Ujistěte se, že jste připojeni k instanci serveru TFS, kterou chcete použít.

2. V diagramu modelování nebo v **Průzkumníku modelů UML**otevřete místní nabídku pro prvek modelu. Vyberte možnost **propojit s pracovní položkou**. Pak vyberte svůj projekt v poli **projekt** .

3. Zvolte jednu nebo více pracovních položek pro propojení s prvkem modelu pomocí jednoho z těchto kroků:

    - Vyberte dotaz v **uloženém dotazu**.

    - Zadejte ID jedné nebo více pracovních položek, které jsou oddělené mezerami v **ID**.

    - Zadejte slovo nebo frázi, která **obsahuje nadpis**.

4. Vyberte **Najít**.

5. V seznamu pracovních položek vyberte pracovní položku nebo pracovní položky, které chcete propojit.

     Až skončíte, vlastnost **work items** elementu model zobrazí větší číslo než dřív. Rovněž se zobrazí ikona na prvku modelu nebo blízko něj.

> [!WARNING]
> Aby bylo možné vytvořit nebo propojit pracovní položku, musíte být již připojeni ke správě zdrojového kódu TFS (SCC). Pokud se pokusíte otevřít připojení k jinému SCC TFS, Visual Studio automaticky zavře aktuální řešení. Před pokusem o vytvoření nebo propojení pracovní položky se ujistěte, že jste již připojeni k odpovídajícímu SCC. V novějších verzích sady Visual Studio nejsou příkazy nabídky k dispozici, pokud nejste připojeni k SCC.

## <a name="OpenWorkItem"></a>Zobrazení pracovních položek propojených s prvkem modelu

1. V **Team Explorer**se ujistěte, že jste připojeni k týmovému projektu, kde jsou pracovní položky propojeny s prvkem modelu.

2. V diagramu modelování nebo v **Průzkumníku modelů UML**otevřete místní nabídku pro prvek modelu. Chcete-li zobrazit seznam propojených pracovních položek, vyberte možnost **Zobrazit pracovní položky** .

    > [!NOTE]
    > Zobrazí se pouze pracovní položky z aktuálně připojeného serveru. Pokud nevidíte žádné pracovní položky, ujistěte se, že jste připojení ke správnému serveru v **Team Explorer**.

## <a name="ViewLinkedModels"></a>Zobrazení elementů modelu propojených s pracovní položkou
 Můžete zobrazit diagramy modelování a prvky, které jsou propojeny s pracovní položkou v Visual Studio Team Services a v Team Foundation Server 2012 nebo novějším. Pracovní položky mohou být například spojený s modely tříd, jež zobrazují návrh nových tříd, které budou implementovány.

1. V **Team Explorer**se ujistěte, že jste připojeni k týmovému projektu, kde jsou prvky modelu propojeny s pracovní položkou.

    > [!NOTE]
    > K prohlížení propojených prvků modelu lze použít pouze Průzkumník týmových projektů, nikoli nástroj Team Web Access. Zkontrolujte, zda je váš pracovní prostor mapován na projekt modelování, který obsahuje prvky nebo diagramy modelování. Pokud nemáte pracovní prostor, je třeba jej vytvořit. Projděte si téma [řešení potíží](#Troubleshooting) a [vytváření pracovních prostorů a práce s nimi](https://msdn.microsoft.com/library/1d7f6ed8-ec7c-48f8-86da-9aea55a90d5a).

2. Otevřete pracovní položku, vyberte možnost **odkazy**. V části **odkaz na model**otevřete místní nabídku elementu propojeného modelu. Vyberte možnost **otevřít propojenou položku**.

     ![Otevřít propojený prvek modelu z pracovní položky](../modeling/media/workitem-openlinkedmodelelement.png "WorkItem_OpenLinkedModelElement")

## <a name="RemoveLinks"></a>Odstranit propojení mezi prvky modelu a pracovními položkami
 Odeberte propojené pracovní položky, přičemž začněte od prvku modelu. Tato operace z pracovní položky odebere vzájemné propojení s daným prvkem modelu. Pokud byste začali s pracovní položkou, k odstranění vzájemných propojení mezi prvkem modelu a pracovní položkou nedojde.

1. V diagramu modelování nebo v **Průzkumníku modelů UML**otevřete místní nabídku pro prvek modelu.

2. Vyberte možnost **odebrat pracovní položky**.

     \- nebo-

    1. Zvolte **vlastnosti**a pak **pracovní položky** , kde se zobrazí počet propojených pracovních položek.

    2. Ve vlastnosti **work items** klikněte na tlačítko se třemi tečkami **[...]** .

        > [!NOTE]
        > Zobrazí se pouze pracovní položky na aktuálním serveru. Pokud je seznam prázdný, ale počet pracovních položek není nula, ujistěte se, že jste připojeni ke správnému serveru v **Team Explorer**.

3. V části **Odebrat odkazy na pracovní položky**vymažte vybrané položky, které chcete odpojit. Klikněte na **tlačítko OK**.

## <a name="Troubleshooting"></a>Při

|**Chybu**|**Možná příčina**|**Rozhodnutí**|
|---------------|------------------------|--------------------|
|Nelze najít prvek modelu, který chcete propojit.|Element může být v diagramu v projektu modelování, který je v [!INCLUDE[esprscc](../includes/esprscc-md.md)]. Pravděpodobně nemáte pracovní prostor, který se mapuje na diagram.|Namapujte pracovní prostor na projekt modelování a diagram. Pokud nemáte pracovní prostor, pak je třeba jej vytvořit.<br /><br /> Chybová zpráva, která se pro tuto chybu objeví, obsahuje cestu, kterou lze namapovat na pracovní prostor.<br /><br /> Viz téma [Vytvoření a práce s pracovními prostory](https://msdn.microsoft.com/library/1d7f6ed8-ec7c-48f8-86da-9aea55a90d5a).|
|Nelze nalézt propojený prvek modelu.|Propojený prvek může být na diagramu, který byl přesunut, přejmenován nebo odstraněn.|1. v pracovní položce odstraňte odkaz na prvek modelu.<br />2. Vytvořte nový odkaz z pracovní položky na prvek modelu.|
|Pracovní položka nemá očekávané propojené prvky modelu.|Pracovní položka ukazuje propojený prvek vrstvy, pouze pokud bylo propojení vytvořeno z pracovní položky. Pokud váš tým nepoužívá [!INCLUDE[esprscc](../includes/esprscc-md.md)], použije se k vytvoření propojení místní cesta k diagramům. Pokud je projekt modelování a jeho diagramy v [!INCLUDE[esprscc](../includes/esprscc-md.md)], všichni členové týmu, kteří mají přístup k projektu, mohou zobrazit propojené prvky v pracovních položkách.|Zkuste aktualizovat pracovní položku.|
|Odstraněním propojení k prvku modelu z pracovní položky neodstraníte propojení prvku modelu s pracovní položkou.||Odstraňte odkaz na pracovní položku, přičemž začněte od prvku modelu.|

## <a name="see-also"></a>Viz také
 [Úprava modelů a diagramů UML](../modeling/edit-uml-models-and-diagrams.md) [vytvoření modelů pro vaši aplikaci](../modeling/create-models-for-your-app.md)
