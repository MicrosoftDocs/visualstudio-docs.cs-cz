---
title: 'Postupy: připojení zobrazení k datům dokumentu | Microsoft Docs'
description: K existujícímu datovému objektu dokumentu může být možné připojit nové zobrazení dokumentu. Pomocí tohoto postupu můžete zjistit, zda lze zobrazení připojit.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- editors [Visual Studio SDK], custom - attach views to document data
ms.assetid: f92c0838-45be-42b8-9c55-713e9bb8df07
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1e044ecbf2309d4d858c16afbdddc130b4661005
ms.sourcegitcommit: d10f37dfdba5d826e7451260c8370fd1efa2c4e4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2020
ms.locfileid: "96994183"
---
# <a name="how-to-attach-views-to-document-data"></a>Postupy: připojení zobrazení k datům dokumentu
Máte-li nové zobrazení dokumentu, může být možné ho připojit k existujícímu datovému objektu dokumentu.

## <a name="to-determine-if-you-can-attach-a-view-to-an-existing-document-data-object"></a>Určení, zda lze připojit zobrazení k existujícímu datovému objektu dokumentu

1. Implementujte <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> .

2. V implementaci nástroje `IVsEditorFactory::CreateEditorInstance` zavolejte `QueryInterface` na existující datový objekt dokumentu, když rozhraní IDE volá vaši `CreateEditorInstance` implementaci.

    Volání `QueryInterface` umožňuje prozkoumávat existující datový objekt dokumentu, který je uveden v `punkDocDataExisting` parametru.

    Přesná rozhraní, která je nutné zadat dotaz, však závisí na editoru, který dokument otevírá, jak je uvedeno v kroku 4.

3. Pokud nenajdete příslušná rozhraní pro existující objekt dat dokumentu, vrátíte kód chyby do editoru, což znamená, že datový objekt dokumentu není kompatibilní s vaším editorem.

    V implementaci integrovaného vývojového prostředí <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> se zobrazí okno se zprávou, že dokument je otevřen v jiném editoru a zeptá se, zda jej chcete zavřít.

4. Pokud tento dokument zavřete, Visual Studio volá vaši továrnu editoru podruhé. U tohoto volání `DocDataExisting` je parametr roven hodnotě null. Vaše implementace objektu pro vytváření vašeho editoru pak může otevřít objekt data dokumentu ve vlastním editoru.

   > [!NOTE]
   > Chcete-li určit, zda můžete pracovat s existujícím objektem dat dokumentu, můžete také použít privátní znalosti implementace rozhraní přetypováním ukazatele na skutečnou [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)] třídu vaší privátní implementace. Například všechny standardní editory implementují `IVsPersistFileFormat` , které dědí z <xref:Microsoft.VisualStudio.OLE.Interop.IPersist> . Proto můžete zavolat `QueryInterface` pro <xref:Microsoft.VisualStudio.OLE.Interop.IPersist.GetClassID%2A> a pokud ID třídy u existujícího datového objektu dokumentu odpovídá ID třídy vaší implementace, můžete pracovat s objektem data dokumentu.

## <a name="robust-programming"></a>Robustní programování
 Když aplikace Visual Studio volá implementaci <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> metody, předává ukazatel na existující datový objekt dokumentu v `punkDocDataExisting` parametru, pokud existuje. Projděte si objekt data dokumentu vrácený v aplikaci `punkDocDataExisting` a určete, zda je datový objekt dokumentu vhodný pro váš editor, jak je uvedeno v poznámce v kroku 4 postupu v tomto tématu. Pokud je to vhodné, váš objekt pro vytváření editoru by měl poskytnout druhý pohled na data, jak je uvedeno v části [Podpora více zobrazení dokumentů](../extensibility/supporting-multiple-document-views.md). V takovém případě by se měla zobrazit příslušná chybová zpráva.

## <a name="see-also"></a>Viz také
- [Podpora více zobrazení dokumentů](../extensibility/supporting-multiple-document-views.md)
- [Zobrazení dat dokumentů a dokumentů ve vlastních editorech](../extensibility/document-data-and-document-view-in-custom-editors.md)
