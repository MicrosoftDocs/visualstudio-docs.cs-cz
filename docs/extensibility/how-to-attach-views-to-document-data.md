---
title: 'Postupy: připojení zobrazení k datům dokumentů | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - attach views to document data
ms.assetid: f92c0838-45be-42b8-9c55-713e9bb8df07
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 46b41c9432970eb9373a80a4e42a92ce82fe9186
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49821341"
---
# <a name="how-to-attach-views-to-document-data"></a>Postupy: připojení zobrazení k datům dokumentu
Pokud máte nové zobrazení dokumentů, je možné připojit k existující objekt dat dokumentu.  
  
## <a name="to-determine-if-you-can-attach-a-view-to-an-existing-document-data-object"></a>Chcete-li zjistit, pokud zobrazení lze připojit k existující objekt dat dokumentu  
  
1. Implementace <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A>.  
  
2. Ve vaší implementaci `IVsEditorFactory::CreateEditorInstance`, volání `QueryInterface` na existující datový objekt dokumentu při volání rozhraní IDE vaše `CreateEditorInstance` implementace.  
  
    Volání `QueryInterface` umožňuje zkoumat data objektu existující dokumentu, který je zadán v `punkDocDataExisting` parametru.  
  
    Přesné rozhraní, které musíte zobrazit dotaz, ale závisí na editor, který je otevření dokumentu, jak je uvedeno v kroku 4.  
  
3. Pokud nenajdete vhodné rozhraní na existující datový objekt dokumentu, vraťte se do editoru označující, že datový objekt dokumentu je nekompatibilní s editor chybový kód.  
  
    V rozhraní IDE provádění <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>, okno se zprávou vás upozorní, že dokument je otevřen v jiném editoru a chcete ho zavřít.  
  
4. Pokud zavřete tento dokument, Visual Studio volá objekt pro vytváření editoru pro podruhé. Na toto volání `DocDataExisting` rovná parametru na hodnotu NULL. Vaše implementace objektu factory editoru pak můžete otevřít datový objekt dokumentu ve vlastním editoru.  
  
   > [!NOTE]
   >  Pokud chcete zjistit, jestli můžete pracovat s existující datový objekt dokumentu, můžete použít také privátní znalost implementace rozhraní přetypováním ukazatel skutečné [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)] třída soukromá implementace. Například implementovat všechny standardní editory `IVsPersistFileFormat`, který dědí z <xref:Microsoft.VisualStudio.OLE.Interop.IPersist>. Proto můžete volat `QueryInterface` pro <xref:Microsoft.VisualStudio.OLE.Interop.IPersist.GetClassID%2A>, a pokud ID třídy na existující objekt dokumentu dat odpovídá vaší implementace ID třídy a pak můžete pracovat se datový objekt dokumentu.  
  
## <a name="robust-programming"></a>Robustní programování  
 Když Visual Studio volá vaši implementaci <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> metody předá zpět ukazatel na existující objekt data dokumentu v `punkDocDataExisting` parametr, pokud existuje. Prozkoumat vrácené v dokumentu datový objekt `punkDocDataExisting` k určení, zda datový objekt dokumentu je vhodná pro váš editor, jak je uvedeno v poznámce v kroku 4 v rámci postupu v tomto tématu. Pokud je vhodné, pak objekt pro vytváření editoru by měla poskytnout druhý zobrazení dat, jak je uvedeno v [podporovat více zobrazení dokumentů](../extensibility/supporting-multiple-document-views.md). Pokud ne, pak by měl zobrazí příslušnou chybovou zprávu.  
  
## <a name="see-also"></a>Viz také:  
 [Podpora více zobrazení dokumentů](../extensibility/supporting-multiple-document-views.md)   
 [Data dokumentu a zobrazení dokumentu ve vlastních editorech](../extensibility/document-data-and-document-view-in-custom-editors.md)