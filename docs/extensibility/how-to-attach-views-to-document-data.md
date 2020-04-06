---
title: 'Postup: Připojení zobrazení k datům dokumentu | Dokumenty společnosti Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - attach views to document data
ms.assetid: f92c0838-45be-42b8-9c55-713e9bb8df07
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1d8bd586a9d67996389f3cb6a2b0f13f0afec3bd
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80711088"
---
# <a name="how-to-attach-views-to-document-data"></a>Postup: Připojení zobrazení k datům dokumentu
Pokud máte nové zobrazení dokumentu, můžete jej připojit k existujícímu datovému objektu dokumentu.

## <a name="to-determine-if-you-can-attach-a-view-to-an-existing-document-data-object"></a>Určení, zda lze připojit zobrazení k existujícímu datovému objektu dokumentu

1. Implementovat <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A>.

2. Při implementaci `IVsEditorFactory::CreateEditorInstance`aplikace `QueryInterface` volání existujícího datového objektu dokumentu `CreateEditorInstance` při volání ide vaše implementace.

    Volání `QueryInterface` umožňuje prozkoumat existující datový objekt dokumentu, `punkDocDataExisting` který je určen v parametru.

    Přesná rozhraní, která je třeba dotaz, však závisí na editor, který je otevření dokumentu, jak je uvedeno v kroku 4.

3. Pokud nenajdete příslušná rozhraní na existující matný objekt dokumentu, vrátí temnou chybu do editoru označující, že datový objekt dokumentu je nekompatibilní s editorem.

    V implementaci <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>rozhraní IDE , okno se zprávou vás upozorní, že dokument je otevřen v jiném editoru a zeptá se, zda chcete zavřít.

4. Pokud zavřete tento dokument, potom Visual Studio volá vaše editor factory podruhé. Při tomto volání `DocDataExisting` je parametr roven hodnotě NULL. Implementace továrny editoru pak můžete otevřít datový objekt dokumentu ve vlastním editoru.

   > [!NOTE]
   > Chcete-li zjistit, zda můžete pracovat s existujícím datovým objektem dokumentu, můžete také [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)] použít soukromé znalosti implementace rozhraní naváděním ukazatele na skutečnou třídu vaší privátní implementace. Například všechny standardní editory implementovat `IVsPersistFileFormat` <xref:Microsoft.VisualStudio.OLE.Interop.IPersist>, který dědí z . Proto můžete volat `QueryInterface` <xref:Microsoft.VisualStudio.OLE.Interop.IPersist.GetClassID%2A>pro , a pokud ID třídy na existující datový objekt dokumentu odpovídá ID třídy implementace, pak můžete pracovat s datovým objektem dokumentu.

## <a name="robust-programming"></a>Robustní programování
 Když Visual Studio volá <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> implementaci metody, předá zpět ukazatel na existující `punkDocDataExisting` datový objekt dokumentu v parametru, pokud existuje. Zkontrolujte datový objekt `punkDocDataExisting` dokumentu vrácený v a zjistěte, zda je datový objekt dokumentu vhodný pro editor, jak je uvedeno v poznámce v kroku 4 postupu v tomto tématu. Pokud je to vhodné, pak editor factory by měl poskytnout druhé zobrazení pro data, jak je uvedeno v [podpora více zobrazení dokumentu](../extensibility/supporting-multiple-document-views.md). Pokud ne, pak by měl zobrazit příslušnou chybovou zprávu.

## <a name="see-also"></a>Viz také
- [Podpora více zobrazení dokumentu](../extensibility/supporting-multiple-document-views.md)
- [Zobrazení dat dokumentů a dokumentů ve vlastních editorech](../extensibility/document-data-and-document-view-in-custom-editors.md)
