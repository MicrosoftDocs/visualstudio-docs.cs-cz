---
title: VSTextBuffer – | Microsoft Docs
description: Objekt VSTextBuffer představuje datový proud textu Unicode, který je obecně přidružený k souboru. Tento článek uvádí rozhraní VSTextBuffer.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- VSTextBuffer
helpviewer_keywords:
- VSTextBuffer object, reference
- views [Visual Studio SDK], VSTextBuffer object
ms.assetid: c5f94b45-7249-4e1f-a53d-1d2a1c61e0ef
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: b3660a8dbb4a0a1280d5a3f428f73f3498244af7
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/25/2021
ms.locfileid: "112905173"
---
# <a name="vstextbuffer-object"></a>VSTextBuffer – objekt
Objekt vyrovnávací paměti textu představuje datový proud textu Unicode, který je obecně přidružený k souboru. Objekt lze použít mimo kontext základního <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> editoru jako v průvodci.

 Následující tabulka ukazuje rozhraní pro `VSTextBuffer` .

|Metoda|Popis|
|------------|-----------------|
|[IOleCommandTarget](/windows/desktop/api/docobj/nn-docobj-iolecommandtarget)|Standardní rozhraní OLE. Používá se ke zpracování příkazu zpět nebo znovu ve vyrovnávací paměti.|
|[Soubor IPersistFile](/windows/desktop/api/objidl/nn-objidl-ipersistfile)|Standardní rozhraní OLE.|
|[IPersistStream](/windows/desktop/api/objidl/nn-objidl-ipersiststream)|Standardní rozhraní OLE.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompoundAction>|Umožňuje vytváření složených akcí (to znamená akcí seskupených v jedné jednotce vrácení zpět nebo znovu).|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData>|Umožňuje trvalost dat dokumentů spravovaných textovou vyrovnávací pamětí.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>|Poskytuje základní služby. používá mnoho klientů.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextFind>|Používá se k prohledávání vyrovnávací paměti.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines>|Poskytuje možnosti čtení a zápisu pomocí dvourozměrných souřadnic. Dědí z `IVsTextBuffer` .|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream>|Poskytuje možnosti čtení a zápisu pomocí jednorozměrných souřadnic. Dědí z `IVsTextBuffer` .|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextScanner>|Poskytuje rychlý sekvenční přístup k textu ve vyrovnávací paměti orientovaný na stream.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsUserData>|Poskytuje přístup k obecné kolekci vlastností. Nejdůležitější vlastností je název nebo moniker vyrovnávací paměti. Do vyrovnávací paměti s tímto rozhraním můžete ukládat vlastní náhodná data tak, že vytvoříte identifikátor GUID a budete je používat jako klíč.|
|<xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer>|Podporuje body připojení pro události.|

## <a name="remarks"></a>Poznámky
 Obvykle `VSTextBuffer` se nachází `QueryInterface` voláním metody `IVsTextBuffer` . Další informace najdete v tématu Vyrovnávací [paměť textu.](/previous-versions/visualstudio/visual-studio-2015/extensibility/accessing-the-text-buffer-by-using-the-legacy-api?preserve-view=true&view=vs-2015)

## <a name="see-also"></a>Viz také
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>
- <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView>
- [Úpravy obrázků](https://www.microsoft.com/download/details.aspx?id=55984)