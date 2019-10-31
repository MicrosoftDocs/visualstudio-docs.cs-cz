---
title: Objekt VSTextBuffer | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- VSTextBuffer
helpviewer_keywords:
- VSTextBuffer object, reference
- views [Visual Studio SDK], VSTextBuffer object
ms.assetid: c5f94b45-7249-4e1f-a53d-1d2a1c61e0ef
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d1895efa9ef10e1e554b98844619507224f09126
ms.sourcegitcommit: 40bd5b27f247a07c2e2514acb293b23d6ce03c29
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2019
ms.locfileid: "73189024"
---
# <a name="vstextbuffer-object"></a>Objekt VSTextBuffer
Objekt textové vyrovnávací paměti představuje datový proud textu v kódu Unicode, který je obecně spojen se souborem. Objekt <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> lze použít vně kontextu základního editoru, jako v průvodci.

 Následující tabulka ukazuje rozhraní `VSTextBuffer`.

|Metoda|Popis|
|------------|-----------------|
|[IOleCommandTarget –](/windows/desktop/api/docobj/nn-docobj-iolecommandtarget)|Standardní rozhraní OLE. Slouží k vrácení zpět nebo opětovnému zpracování ve vyrovnávací paměti.|
|[IPersistFile](/windows/desktop/api/objidl/nn-objidl-ipersistfile)|Standardní rozhraní OLE.|
|[IPersistStream](/windows/desktop/api/objidl/nn-objidl-ipersiststream)|Standardní rozhraní OLE.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompoundAction>|Umožňuje vytváření akcí sloučenin (tj. akcí, které jsou seskupeny do jedné jednotky akce zpět/znovu).|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData>|Umožňuje trvalá data dokumentu spravovaná vyrovnávací pamětí textu.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>|Poskytuje základní služby; používá mnoho klientů.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextFind>|Používá se k prohledání vyrovnávací paměti.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines>|Poskytuje funkce pro čtení a zápis pomocí dvourozměrných souřadnic. Dědí z `IVsTextBuffer`.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream>|Poskytuje funkce pro čtení a zápis s použitím jednorozměrné souřadnice. Dědí z `IVsTextBuffer`.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextScanner>|Poskytuje rychlý a sekvenční přístup k textu ve vyrovnávací paměti, který je orientovaný na proud.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsUserData>|Poskytuje přístup k obecné kolekci vlastností. Nejdůležitější vlastností je název nebo moniker vyrovnávací paměti. Vlastní náhodná data můžete do vyrovnávací paměti ukládat pomocí tohoto rozhraní tak, že vytvoříte identifikátor GUID a použijete ho jako klíč.|
|<xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer>|Podporuje body připojení pro události.|

## <a name="remarks"></a>Poznámky
 `VSTextBuffer` se obvykle nachází v `QueryInterface` volání `IVsTextBuffer`. Další informace najdete v tématu [vyrovnávací paměť textu](/visualstudio/extensibility/accessing-the-text-buffer-by-using-the-legacy-api?view=vs-2015).

## <a name="see-also"></a>Viz také:
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>
- <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView>
- [Úpravy obrázků](https://www.microsoft.com/download/details.aspx?id=55984)