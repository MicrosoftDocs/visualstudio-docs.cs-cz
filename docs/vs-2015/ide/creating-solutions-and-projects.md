---
title: Vytváření projektů a řešení | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
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
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 336fb41ee6a4c90e7065187b2805aefe9e6e6df7
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49893699"
---
# <a name="creating-solutions-and-projects"></a>Vytváření řešení a projektů
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Projekty jsou logické kontejnery pro všechno, co potřebujete k sestavení aplikace. Při vytváření projektu výběrem **souboru &#124; nový &#124; projektu** v hlavní nabídce [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] vytvoří řešení, které ho obsahuje. Potom přidáte další nové nebo existující projekty do řešení v případě potřeby. Můžete vytvářet projekty z existujících souborů kódu a můžete vytvořit dočasné projekty (pouze .NET), který bude odstraněn, až budete hotovi s nimi.  
  
> [!NOTE]
>  Popisy v tomto tématu jsou založeny na Visual Studio Community edition. Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch zde popsaných v závislosti na vašem nastavení nebo verzi systému Visual Studio. Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky. Další informace najdete v tématu [přizpůsobení nastavení pro vývoj v sadě Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## <a name="create-a-project-from-an-installed-project-template"></a>Vytvoření projektu ze šablony projektu nainstalované  
 **Soubor &#124; nový &#124; projektu** v hlavní nabídce zobrazíte dialogové okno Nový projekt. V levém podokně v části **Intalled &#124; šablony** zvolili programovací jazyk a platformu nebo technologii, a potom vyberte z dostupných šablon v prostředním podokně.  
  
 V **nový projekt** dialogového okna, **řešení** rozevíracího seznamu nabízí možnost vytvořit nový projekt v řešení novou nebo existující, nebo v nové instanci sady Visual Studio.  
  
## <a name="create-a-project-from-existing-code-files"></a>Vytvoření projektu z existujících souborů kódu  
 Pokud máte kolekci dojde ke ztrátě zdrojových souborů, můžete snadno vytvořit projekt, který je obsahuje. Zvolte **souboru &#124; nový &#124;projekt z existujícího kódu** spustit **vytvořit projekt z existujících souborů kódu pomocí průvodce** a postupujte podle zobrazených výzev.  
  
> [!TIP]
>  Tato možnost je nejvhodnější pro poměrně jednoduchá kolekce souborů.  
  
## <a name="create-a-temporary-project-c-and-visual-basic"></a>Vytvoření dočasného projektu (C# a Visual Basic)  
 Při práci s dočasné projekty, můžete vytvořit a experimentovat s projektem .NET bez zadání umístění na disku. Při vytváření projektu stačí vyberte typ projektu a šablonu a zadejte název do **nový projekt** dialogové okno. Kdykoli při práci s dočasný projekt, ho můžete uložit nebo ho zahodit.  
  
## <a name="create-a-net-project-that-targets-a-specific-version-of-the-net-framework"></a>Vytvořit projekt .NET, který cílí na konkrétní verzi rozhraní .NET Framework  
 Můžete vytvořit projekt, který cíleny na starší verze rozhraní .NET Framework pomocí **rozhraní .NET Framework** verze rozevírací nabídce v horní části **nový projekt** dialogové okno. Nastavte tuto hodnotu před výběrem šablony projektu, například pouze šablony, které jsou kompatibilní s touto verzí rozhraní .NET Framework, se zobrazí v seznamu.  
  
 Musíte mít rozhraní .NET Framework 3.5 v systému nainstalovány pro přístup k rozhraní framework verze starší než 4.0.  
  
## <a name="downloading-sample-solutions"></a>Stažení ukázkové řešení  
 Visual Studio můžete použít ke stažení a instalaci ukázkové řešení od [galerie kódů MSDN](http://go.microsoft.com/fwlink/?LinkId=254185).  
  
 Ukázky lze stáhnout jednotlivě nebo lze stáhnout balík ukázek, který obsahuje související ukázky sdílející technologii nebo téma. Obdržíte oznámení, když změny zdrojového kódu budou publikovány pro libovolnou ukázku, kterou stáhnete.  
  
 Další informace najdete v tématu [ukázky sady Visual Studio](../ide/visual-studio-samples.md).  
  
## <a name="adding-single-files-at-the-solution-level"></a>Přidání jednotlivé soubory na úrovni řešení  
 Někdy je nutné soubor, na který odkazovat více projektů nebo, který obsahuje text nebo různých dat, které logicky patří na úrovni řešení, nikoli v konkrétním projektu.  Chcete-li přidat jednu položku řešení:  
  
1.  Klikněte pravým tlačítkem na uzel řešení v **Průzkumníka řešení** a zvolte **přidat &#124; nová položka** nebo **přidat &#124; existující položku**.  
  
## <a name="creating-empty-solutions"></a>Vytvoření prázdných řešení  
 I když projekt musí být umístěn v řešení, můžete vytvořit řešení, která nemá žádné projekty.  
  
#### <a name="to-create-an-empty-solution"></a>Vytvoření prázdného řešení  
  
1. Na **souboru** nabídky, klikněte na tlačítko **nový** a potom klikněte na tlačítko **nový projekt**.  
  
2. V levém podokně vyberte **nainstalováno**vyberte **ostatní typy projektů**a pak vyberte **řešení sady Visual Studio** z rozbaleného seznamu.  
  
3. V prostředním podokně vyberte **prázdné řešení**.  
  
4. Nastavte **název** a **umístění** hodnoty pro vaše řešení, pak klikněte na **OK**.  
  
   Po vytvoření prázdného řešení můžete přidat nové nebo existující projekty nebo položky k němu kliknutím **přidat novou položku** nebo **přidat existující položku** na **projektu** nabídky.  
  
### <a name="deleting-solutions"></a>Odstraňuje se řešení  
 Řešení můžete odstranit trvale, ale ne prostřednictvím [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Před odstraněním řešení, přesuňte všechny projekty, které můžete chtít znovu použít v jiné řešení. Potom k odstranění adresáře, který obsahuje soubory řešení .sln a .suo, použijte Průzkumník souborů.  
  
> [!NOTE]
>  Soubor .suo je skrytý soubor, který není ve výchozím nastavení Průzkumníku souborů zobrazen.  
  
##### <a name="to-delete-a-solution"></a>Odstranit řešení  
  
1.  V **Průzkumníka řešení**, klikněte pravým tlačítkem na řešení, které chcete odstranit a vyberte **otevřít složku v Průzkumníku souborů**.  
  
2.  V Průzkumníku souborů přejděte o jednu úroveň výše.  
  
3.  Vyberte adresář, který obsahuje řešení a stiskněte klávesu Delete.  
  
## <a name="see-also"></a>Viz také  
 [Řešení a projekty](../ide/solutions-and-projects-in-visual-studio.md)   
 [NIB postupy: vytváření řešení vícenásobného projektu](http://msdn.microsoft.com/en-us/02ecd6dd-0114-46fe-b335-ba9c5e3020d6)



