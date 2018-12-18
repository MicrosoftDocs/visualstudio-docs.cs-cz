---
title: Podpora více zobrazení dokumentů | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], custom - multiple document views
ms.assetid: c7ec2366-91c4-477f-908d-e89068bdb3e3
caps.latest.revision: 26
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 6be1e48917c8ad5e7035f01caa4f74b78a6fa3d0
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51792252"
---
# <a name="supporting-multiple-document-views"></a>Podpora více zobrazení dokumentů
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Můžete zadat více než jedno zobrazení dokumentu tak, že vytvoříte samostatný dokument dat a objektů zobrazení dokumentu pro editor. Jsou některé případy, ve kterých by bylo užitečné další dokument zobrazení:  
  
- Nové okno podpory: Chcete váš editor, který poskytuje dvě nebo více zobrazení stejného typu, tak, aby uživatel, který už má okno otevře v editoru můžete otevřít nové okno tak, že vyberete **nové okno** příkaz **okno** nabídky.  
  
- Formuláře a kódu zobrazit podpory: Chcete, aby váš editor, který poskytuje různé typy zobrazení. [!INCLUDE[vbprvb](../includes/vbprvb-md.md)], například poskytuje zobrazení formuláře a zobrazení kódu.  
  
  Další informace o tom naleznete v postupu CreateEditorInstance v souboru EditorFactory.cs ve vlastním editoru projekt vytvořený v rámci Visual Studio balíček šablony. Další informace o tomto projektu naleznete v tématu [návod: vytvoření vlastního editoru](../extensibility/walkthrough-creating-a-custom-editor.md).  
  
## <a name="synchronizing-views"></a>Synchronizace zobrazení  
 Při implementaci více zobrazení je datový objekt dokumentu odpovídá za pořízení všechna zobrazení, které jsou synchronizovány s daty. Můžete použít zpracování rozhraní na událostí <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> pro synchronizaci více zobrazení s daty.  
  
 Pokud použijete <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> objektu pro synchronizaci více zobrazení, pak musíte implementovat vlastní systém událostí ke zpracování změny provedené na datový objekt dokumentu. Různé úrovně členitosti můžete použít k zajištění aktuálnosti několik zobrazení. Nastavení maximální členitosti, při psaní v jednom zobrazení se aktualizují ostatní zobrazení okamžitě. S minimální členitost nebudou aktualizovány jiných zobrazení, dokud se aktivují.  
  
## <a name="determining-whether-document-data-is-already-open"></a>Určení, zda Data dokumentu je již otevřen  
 Spuštěnou tabulku dokumentů (r...) v integrovaném vývojovém prostředí (IDE) pomáhá sledovat, jestli dat pro dokument je už otevřený, jak je znázorněno v následujícím diagramu.  
  
 ![DocDataView – grafika](../extensibility/media/docdataview.gif "DocDataView –")  
Více zobrazení  
  
 Ve výchozím nastavení, každé zobrazení (objekt zobrazení dokumentu) je součástí vlastní okna rámce (<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame>). Jak už jsme zmínili ale data dokumentu lze zobrazit více zobrazení. Visual Studio povolit, rozlišuje rámcový zjistit, jestli dokument dotyčný je již otevřen v editoru. Když se volá rozhraní IDE <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> vytvoření editoru, vrátí NENULOVOU hodnotu v `punkDocDataExisting` parametr označuje, že dokument je již otevřen v jiném editoru. Další informace o tom, naleznete v tématu funkce rámcový [spuštěná tabulka dokumentů](../extensibility/internals/running-document-table.md).  
  
 Ve vaší <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> implementace, zkontrolujte dokumentu datový objekt vrácený v `punkDocDataExisting` k určení, zda je vhodné pro editor dat dokumentu. (Například pouze data ve formátu HTML mají být zobrazeny editoru HTML.) Pokud je vhodné, pak objekt pro vytváření editoru by měl zviditelňují druhý pro data. Pokud `punkDocDataExisting` parametr není `NULL`, je možné buď, že datový objekt dokument je otevřen v jiném editoru, nebo, pravděpodobnější, data dokumentu je již otevřen v jiné zobrazení se stejným editoru. Pokud data dokument je otevřen v jiný editor, který nepodporuje objekt pro vytváření editoru, Visual Studio nelze ji otevřít objekt pro vytváření editoru. Další informace najdete v tématu [postupy: připojení zobrazení k datům dokumentu](../extensibility/how-to-attach-views-to-document-data.md).

