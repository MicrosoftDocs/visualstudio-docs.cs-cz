---
title: Podpora více zobrazení dokumentů | Microsoft Docs
description: Naučte se, jak poskytnout více než jedno zobrazení dokumentu pomocí samostatných dat dokumentů a objektů zobrazení dokumentů pro vlastní editor v sadě Visual Studio SDK.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - multiple document views
ms.assetid: c7ec2366-91c4-477f-908d-e89068bdb3e3
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 5360f67714e1da4f7372ee51eb4f75cc8835c1fd
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99965119"
---
# <a name="supporting-multiple-document-views"></a>Podpora více zobrazení dokumentů
Můžete poskytnout více než jedno zobrazení dokumentu vytvořením samostatného dokumentu a objektů zobrazení dokumentu pro Editor. V některých případech může být užitečné další zobrazení dokumentu:

- Podpora nového okna: Chcete, aby Editor poskytoval dvě nebo více zobrazení stejného typu, takže uživatel, který již má otevřené okno v editoru, může otevřít nové okno výběrem příkazu **Nový okno** v nabídce **okno** .

- Podpora zobrazení formulářů a kódu: Chcete, aby Editor poskytoval zobrazení různých typů. [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]například poskytuje jak zobrazení formuláře, tak zobrazení kódu.

  Další informace o tomto postupu naleznete v tématu CreateEditorInstance v souboru EditorFactory.cs v projektu vlastního editoru vytvořeném šablonou balíčku sady Visual Studio. Další informace o tomto projektu naleznete v tématu [Návod: Vytvoření vlastního editoru](../extensibility/walkthrough-creating-a-custom-editor.md).

## <a name="synchronizing-views"></a>Synchronizace zobrazení
 Při implementaci více zobrazení zodpovídá datový objekt dokumentu za účelem zachování všech zobrazení synchronizovaných s daty. Rozhraní pro zpracování událostí v nástroji můžete použít <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> k synchronizaci více zobrazení s daty.

 Pokud nepoužíváte <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> objekt k synchronizaci více zobrazení, je nutné implementovat vlastní systém událostí pro zpracování změn provedených v datovém objektu dokumentu. Můžete použít různé úrovně členitosti a udržovat tak více zobrazení v aktuálním stavu. Při nastavení maximální členitosti při psaní v jednom zobrazení se další zobrazení aktualizují hned. S minimálními členitosti nejsou další zobrazení aktualizována, dokud nejsou aktivována.

## <a name="determining-whether-document-data-is-already-open"></a>Určení, jestli jsou data dokumentu už otevřená
 Běžící tabulka dokumentů (RDT) v integrovaném vývojovém prostředí (IDE) pomáhá sledovat, zda jsou data dokumentu již otevřena, jak je znázorněno v následujícím diagramu.

 ![Obrázek DocDataView](../extensibility/media/docdataview.gif "Docdataview") Více zobrazení

 Ve výchozím nastavení je každé zobrazení (objekt zobrazení dokumentu) obsaženo ve vlastním snímku okna ( <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> ). Jak už bylo uvedeno, data dokumentu se ale dají zobrazit ve více zobrazeních. Chcete-li tuto možnost povolit, Visual Studio zkontroluje RDT a určí, zda je již dokument otevřen v editoru. Když rozhraní IDE vyvolá <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> možnost vytvořit editor, hodnota jiná než null vrácená v `punkDocDataExisting` parametru označuje, že dokument je již otevřen v jiném editoru. Další informace o tom, jak funkce RDT, najdete v tématu [Spuštění tabulky dokumentů](../extensibility/internals/running-document-table.md).

 V rámci <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> implementace zkontrolujte datový objekt dokumentu vrácený v `punkDocDataExisting` a určete, zda jsou data dokumentu vhodná pro váš editor. (Například editor HTML by měl zobrazovat pouze data HTML.) Pokud je to vhodné, váš objekt pro vytváření editoru by měl pro data poskytnout druhý pohled. Pokud `punkDocDataExisting` parametr není `NULL` , je možné, že datový objekt dokumentu je otevřen v jiném editoru nebo je pravděpodobnější, že data dokumentu již jsou otevřena v jiném zobrazení se stejným editorem. Pokud jsou data dokumentu otevřená v jiném editoru, který váš objekt pro vytváření editor nepodporuje, Visual Studio se nepodařilo otevřít objekt pro vytváření editoru. Další informace najdete v tématu [Postup: připojení zobrazení k datům dokumentů](../extensibility/how-to-attach-views-to-document-data.md).
