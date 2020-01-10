---
title: Vytváření řešení a projektů | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- vs.openprojectfromweb
- vs.newproject
- VS.ToolsOptionsPages.Projects.General
- SolutionItemsProject
helpviewer_keywords:
- solutions [Visual Studio], deleting
- solutions [Visual Studio], creating
- projects [Visual Studio], creating
ms.assetid: 836f8ca0-3fc9-4f4b-9090-45f2e4d2e9c8
caps.latest.revision: 49
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 10375e00eb850691e88d01c56a87bb967c40e9ea
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/10/2020
ms.locfileid: "75850572"
---
# <a name="creating-solutions-and-projects"></a>Vytváření řešení a projektů
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Projekty jsou logické kontejnery pro všechno, co je potřeba k sestavení aplikace. Když vytváříte projekt výběrem možnosti  **&#124; soubor nový &#124; projekt** z hlavní nabídky, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] vytvoří řešení, které ho bude obsahovat. V případě potřeby můžete do řešení přidat další nové nebo existující projekty. Můžete vytvořit projekty z existujících souborů kódu a můžete vytvořit dočasné projekty (pouze .NET), které budou odstraněny, až budete s nimi hotovi.

> [!NOTE]
> Popisy v tomto tématu jsou založeny na Visual Studio Community edition. Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch zde popsaných v závislosti na vašem nastavení nebo verzi systému Visual Studio. Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky. Další informace najdete v tématu [přizpůsobení nastavení pro vývoj v sadě Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).

## <a name="create-a-project-from-an-installed-project-template"></a>Vytvoření projektu z nainstalované šablony projektu
 **Soubor &#124; nový &#124; projekt** z hlavní nabídky k vytvoření dialogového okna Nový projekt. V levém podokně v části  **&#124; nespravované šablony** zvolte programovací jazyk a platformu nebo technologii a pak vyberte z dostupných šablon v prostředním podokně.

 V dialogovém okně **Nový projekt** vám rozevírací seznam **řešení** nabízí možnost vytvořit nový projekt v novém nebo existujícím řešení nebo v nové instanci sady Visual Studio.

## <a name="create-a-project-from-existing-code-files"></a>Vytvoření projektu z existujících souborů kódu
 Máte-li kolekci volných zdrojových souborů, můžete snadno vytvořit projekt, který je obsahuje. Zvolením možnosti **soubor &#124; nový &#124;projekt z existujícího kódu** spusťte **Průvodce vytvořením projektu z existujících souborů kódu** a postupujte podle zobrazených výzev.

> [!TIP]
> Tato možnost funguje nejlépe pro relativně jednoduché kolekce souborů.

## <a name="create-a-temporary-project-c-and-visual-basic"></a>Vytvoření dočasného projektu (C# a Visual Basic)
 Při práci s dočasnými projekty můžete vytvořit a experimentovat s projektem .NET bez určení umístění na disku. Při vytváření projektu stačí vybrat typ projektu a šablonu a zadat název v dialogovém okně **Nový projekt** . Kdykoli při práci s dočasným projektem, můžete ho uložit, nebo ho můžete zahodit.

## <a name="create-a-net-project-that-targets-a-specific-version-of-the-net-framework"></a>Vytvořit projekt .NET, který cílí na konkrétní verzi rozhraní .NET Framework
 Můžete vytvořit projekt, který bude cílit na starší verze .NET Framework pomocí rozevírací nabídky **.NET Framework** verze v horní části dialogového okna **Nový projekt** . Před výběrem šablony projektu nastavte tuto hodnotu, protože v seznamu se zobrazí pouze šablony kompatibilní s tímto .NET Framework verzí.

 Musíte mít ve svém systému nainstalovaný .NET Framework 3,5 pro přístup k verzím rozhraní starším než 4,0.

## <a name="downloading-sample-solutions"></a>Stažení ukázkových řešení
 Pomocí sady Visual Studio můžete stáhnout a nainstalovat ukázková řešení z [Galerie kódu na webu MSDN](https://code.msdn.microsoft.com/).

 Ukázky lze stáhnout jednotlivě nebo lze stáhnout balík ukázek, který obsahuje související ukázky sdílející technologii nebo téma. Obdržíte oznámení, když změny zdrojového kódu budou publikovány pro libovolnou ukázku, kterou stáhnete.

 Další informace najdete v tématu [ukázky sady Visual Studio](../ide/visual-studio-samples.md).

## <a name="adding-single-files-at-the-solution-level"></a>Přidávání jednotlivých souborů na úrovni řešení
 Někdy je možné, že máte soubor, na který se odkazuje více projektů, nebo obsahuje text nebo různá data, která logicky náležejí na úrovni řešení, nikoli v rámci konkrétního projektu.  Přidání jedné položky do řešení:

1. Klikněte pravým tlačítkem myši na uzel řešení v **Průzkumník řešení** a vyberte možnost  **&#124; přidat novou položku** nebo **Přidat &#124; existující položku**.

## <a name="creating-empty-solutions"></a>Vytvoření prázdných řešení
 I když se projekt musí nacházet v řešení, můžete vytvořit řešení, které nemá žádné projekty.

#### <a name="to-create-an-empty-solution"></a>Vytvoření prázdného řešení

1. V nabídce **soubor** klikněte na příkaz **Nový** a potom klikněte na **Nový projekt**.

2. V levém podokně vyberte **nainstalovat**, vyberte **jiné typy projektů**a potom v rozbaleném seznamu vyberte **řešení sady Visual Studio** .

3. V prostředním podokně vyberte **prázdné řešení**.

4. Nastavte **název** a hodnoty **umístění** pro vaše řešení a pak klikněte na **OK**.

   Po vytvoření prázdného řešení můžete do něj přidat nové nebo existující projekty nebo položky kliknutím na tlačítko **Přidat novou položku** nebo **Přidat existující položku** v nabídce **projekt** .

### <a name="deleting-solutions"></a>Odstraňování řešení
 Řešení můžete odstranit trvale, ale ne pomocí [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Před odstraněním řešení přesuňte všechny projekty, které byste mohli chtít znovu použít v jiném řešení. Potom k odstranění adresáře, který obsahuje soubory řešení .sln a .suo, použijte Průzkumník souborů.

> [!NOTE]
> Soubor .suo je skrytý soubor, který není ve výchozím nastavení Průzkumníku souborů zobrazen.

##### <a name="to-delete-a-solution"></a>Odstranění řešení

1. V **Průzkumník řešení**klikněte pravým tlačítkem myši na řešení, které chcete odstranit, a vyberte možnost **Otevřít složku v Průzkumníku souborů**.

2. V Průzkumníku souborů přejděte o jednu úroveň výše.

3. Vyberte adresář obsahující řešení a stiskněte klávesu DELETE.

## <a name="see-also"></a>Viz také
 [Řešení a projekty](../ide/solutions-and-projects-in-visual-studio.md) [NIB postupy: vytváření řešení s více projekty](https://msdn.microsoft.com/02ecd6dd-0114-46fe-b335-ba9c5e3020d6)
