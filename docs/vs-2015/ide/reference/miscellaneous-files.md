---
title: Různé soubory | Dokumentace Microsoftu
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
- VS.newfile
- VS.OpenWith
- MiscellaneousFilesProject
helpviewer_keywords:
- solutions, miscellaneous files
- builds [Visual Studio], miscellaneous files
- standalone files
- Solution Explorer, miscellaneous files
- Miscellaneous Files folder
- files [Visual Studio], outside of containers
- files [Visual Studio], Miscellaneous Files folder
ms.assetid: 5b96640b-8efe-48a4-8d0a-1ae3f9587e44
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: cb9c7fb46517ff2d6dffdeb0cedfc4982c1f3366
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49258478"
---
# <a name="miscellaneous-files"></a>Ostatní soubory
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
Můžete chtít použít [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] editory pracovat nezávisle na soubory z projektu nebo řešení. Když máte řešení otevřené, můžete otevřít a upravit soubory bez jejich přidání do řešení nebo projektu. Soubory, které chcete pracovat s nezávisle na kontejnery se nazývají různé soubory. Různé soubory jsou externí vzhledem k řešení a projektů, nejsou zahrnuty v sestavení a nemůže být součástí řešení pod správou zdrojových kódů.  
  
 Otevírání souborů nezávisle z kontejneru je užitečné pro celou řadu důvodů. Můžete mít soubor, který chcete zobrazit při vývoji řešení založené na projektu, ale není celočíselný k vývoji tohoto řešení. Běžné příklady vývojové poznámky nebo pokynů, schéma databáze a klipů kódu. Kromě toho můžete vytvořit samostatný soubor.  
  
 ![Projekty řešení](../../ide/reference/media/projects-solutions-misc.gif "Projects_Solutions_Misc")  
  
 Průzkumník řešení zobrazíte složku různé soubory pro soubory, když jsou povolené možnosti pro složku. Možnosti můžete nastavit [dokumenty, prostředí, dialogové okno Možnosti](../../ide/reference/documents-environment-options-dialog-box.md). Po zavření souboru různé není přidružené žádné konkrétní řešení nebo projektu, pokud možnost není povolena pro, který také.  
  
 Ve složce ostatní soubory představuje soubory jako odkazy. I když tato složka není součástí řešení, když otevřete řešení, některé nebo všechny ostatní soubory, které byly otevřeny při posledním zavření řešení jsou znovu otevřít, v závislosti na nastavení pro složku.  
  
> [!NOTE]
>  Některé soubory, které nejsou uvedeny ve složce ostatní soubory jsou soubory, které nelze upravovat v rámci rozhraní IDE, jako jsou soubory ZIP a DOC soubory. Integrované vývojové prostředí nebude sledovat soubory, které lze upravovat pouze prostřednictvím externího editoru.  
  
## <a name="commands-available-in-the-ide"></a>Příkazy, které jsou k dispozici v integrovaném vývojovém prostředí  
 Nabídky, panely nástrojů a příkazy obsahují mění v závislosti na formát souboru je otevřít. Když otevřete textový soubor, například se zobrazí panelu nástrojů textového editoru a jeho příkazy jsou k dispozici. Když potom otevřete soubor schématu XML, zobrazí se panel nástrojů schématu XML. Při úpravách schématu XML, nejsou k dispozici příkazy nástrojů textového editoru (nebo na panelu nástrojů, samotné). Schéma XML je aktivní okno a v důsledku toho se kontext aktuálního výběru. Při přepínání mezi soubor projektu a soubor různé všechny příkazy související s projektem zmizí a zobrazí pouze ty, které jsou přímo souvisí s různé souboru.  
  
## <a name="folder-display-options"></a>Možnosti zobrazení složky  
 Možnosti zobrazení pro různé složky můžete nastavit tak, aby složka se zobrazí i v případě, že všechny ostatní soubory ještě nebyl otevřen. Soubor řešení nedokáže spravovat trvale seznam různých souborů. Používá volitelná funkce, které umožňuje mějte na paměti na uživatele naposledy použité (MRU) seznam souborů.  
  
## <a name="see-also"></a>Viz také  
 [Řešení a projekty](../../ide/solutions-and-projects-in-visual-studio.md)   
 [Dokumenty, Prostředí, dialogové okno Možnosti](../../ide/reference/documents-environment-options-dialog-box.md)



