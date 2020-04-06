---
title: Objekt VSTextBuffer | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- VSTextBuffer
helpviewer_keywords:
- VSTextBuffer object, reference
- views [Visual Studio SDK], VSTextBuffer object
ms.assetid: c5f94b45-7249-4e1f-a53d-1d2a1c61e0ef
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a5ea44d2b22c96d49f334f2ea33f9db8d69b5eb0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697727"
---
# <a name="vstextbuffer-object"></a>Objekt VSTextBuffer
Objekt vyrovnávací paměti textu představuje datový proud textu Unicode, který je obecně spojen se souborem. Objekt <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> lze použít mimo kontext editoru jádra, jako v průvodci.

 V následující tabulce jsou `VSTextBuffer`uvedena rozhraní aplikace .

|Metoda|Popis|
|------------|-----------------|
|[IOleCommandTarget](/windows/desktop/api/docobj/nn-docobj-iolecommandtarget)|Standardní rozhraní OLE. Používá se pro zpracování vrátit nebo znovu provést ve vyrovnávací paměti.|
|[Soubor IPersistFile](/windows/desktop/api/objidl/nn-objidl-ipersistfile)|Standardní rozhraní OLE.|
|[IPersistStream](/windows/desktop/api/objidl/nn-objidl-ipersiststream)|Standardní rozhraní OLE.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompoundAction>|Umožňuje vytváření akcí složených sloučenin (to znamená akce, které jsou seskupeny do jedné jednotky vrátit nebo znovu).|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData>|Umožňuje trvalost dat dokumentu spravovaných textovou vyrovnávací pamětí.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>|Poskytuje základní služby; používá mnoho klientů.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextFind>|Slouží k prohledání vyrovnávací paměti.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines>|Poskytuje možnosti čtení a zápisu pomocí dvourozměrných souřadnic. Dědí `IVsTextBuffer`z .|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream>|Poskytuje možnosti čtení a zápisu pomocí jednorozměrných souřadnic. Dědí `IVsTextBuffer`z .|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextScanner>|Poskytuje rychlý, stream orientovaný, sekvenční přístup k textu ve vyrovnávací paměti.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsUserData>|Poskytuje přístup k obecné kolekci vlastností. Nejdůležitější vlastností je název nebo zástupné názvy vyrovnávací paměti. Vlastní náhodná data můžete uložit do vyrovnávací paměti s tímto rozhraním vytvořením identifikátoru GUID a jeho použitím jako klíče.|
|<xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer>|Podporuje spojovací body pro události.|

## <a name="remarks"></a>Poznámky
 Obvykle `VSTextBuffer` se nachází `QueryInterface` volání `IVsTextBuffer`na . Další informace naleznete v [tématu Text buffer](/visualstudio/extensibility/accessing-the-text-buffer-by-using-the-legacy-api?view=vs-2015).

## <a name="see-also"></a>Viz také
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>
- <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView>
- [Úpravy obrázků](https://www.microsoft.com/download/details.aspx?id=55984)
