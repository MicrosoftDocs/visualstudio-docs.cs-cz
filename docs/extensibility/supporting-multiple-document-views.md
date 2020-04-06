---
title: Podpora zobrazení více dokumentů | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - multiple document views
ms.assetid: c7ec2366-91c4-477f-908d-e89068bdb3e3
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a952414fa7156d80675564e519e556ccedd524a3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80699538"
---
# <a name="supporting-multiple-document-views"></a>Podpora více zobrazení dokumentů
Vytvořením samostatných dat dokumentu a objektů zobrazení dokumentu pro editor můžete vytvořit více než jedno zobrazení dokumentu. Některé případy, ve kterých by bylo užitečné další zobrazení dokumentu, jsou:

- Nová podpora oken: Chcete, aby editor poskytoval dvě nebo více zobrazení stejného typu, aby uživatel, který již má otevřené okno v editoru, mohl otevřít nové okno výběrem příkazu **Nové okno** z nabídky **Okno.**

- Podpora zobrazení formuláře a kódu: Chcete, aby editor poskytoval zobrazení různých typů. [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)], například poskytuje zobrazení formuláře i zobrazení kódu.

  Další informace o tomto, naleznete v souboru CreateEditorInstance v souboru EditorFactory.cs v projektu vlastního editoru vytvořeného šablonou balíčku Sady Visual Studio. Další informace o tomto projektu naleznete v [tématu Návod: Vytvoření vlastního editoru](../extensibility/walkthrough-creating-a-custom-editor.md).

## <a name="synchronizing-views"></a>Synchronizace zobrazení
 Při implementaci více zobrazení je datový objekt dokumentu zodpovědný za synchronizaci všech zobrazení s daty. Rozhraní pro zpracování událostí můžete <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> použít k synchronizaci více zobrazení s daty.

 Pokud nepoužijete <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> objekt k synchronizaci více zobrazení, je nutné implementovat vlastní systém událostí pro zpracování změn provedených v datovém objektu dokumentu. Můžete použít různé úrovně rozlišovací schopnost udržovat více zobrazení aktuální. Při nastavení maximální rozlišovací schopnost, při psaní v jednom zobrazení jsou ostatní zobrazení okamžitě aktualizována. S minimální rozlišovací schopnost, ostatní zobrazení nejsou aktualizovány, dokud nejsou aktivovány.

## <a name="determining-whether-document-data-is-already-open"></a>Určení, zda jsou data dokumentu již otevřena
 Spuštěná tabulka dokumentů (RDT) v integrovaném vývojovém prostředí (IDE) pomáhá sledovat, zda jsou data dokumentu již otevřená, jak je znázorněno na následujícím diagramu.

 ![DocDataView , grafika](../extensibility/media/docdataview.gif "Zobrazení Docdata") Více zobrazení

 Ve výchozím nastavení je každé zobrazení (objekt zobrazení dokumentu)<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame>obsaženo ve vlastním rámečku okna ( ). Jak již bylo uvedeno, data dokumentu však mohou být zobrazena ve více zobrazeních. Chcete-li povolit, Visual Studio zkontroluje RDT k určení, zda je dotyčný dokument již otevřen v editoru. Při volání <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> ide k vytvoření editoru, non-NULL `punkDocDataExisting` hodnota vrácená v parametru označuje, že dokument je již otevřen v jiném editoru. Další informace o tom, jak rdt funguje, naleznete [v tématu Spuštění tabulky dokumentů](../extensibility/internals/running-document-table.md).

 V <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> implementaci zkontrolujte datový objekt `punkDocDataExisting` dokumentu vrácené v k určení, zda data dokumentu je vhodné pro editor. (Například editor HTML by měl zobrazovat pouze data HTML.) Pokud je to vhodné, pak editor factory by měl poskytnout druhé zobrazení pro data. Pokud `punkDocDataExisting` parametr není `NULL`, je možné, že datový objekt dokumentu je otevřen v jiném editoru, nebo, spíše, že data dokumentu je již otevřena v jiném zobrazení se stejným editorem. Pokud jsou data dokumentu otevřena v jiném editoru, který vaše editor factory nepodporuje, pak Visual Studio se nepodaří otevřít editor factory. Další informace naleznete v [tématu How to: Attach Views to Document Data](../extensibility/how-to-attach-views-to-document-data.md).
