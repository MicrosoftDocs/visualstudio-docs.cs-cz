---
title: 'Postup: Správa soukromé galerie pomocí nastavení registru | Dokumenty společnosti Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSIX private galleries, managing
- managing VSIX private galleries
ms.assetid: 86b86442-4293-4cad-9fe2-876eef65f426
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a2630fc71bea40a4d05e616ae336759ba62431a0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710936"
---
# <a name="how-to-manage-a-private-gallery-by-using-registry-settings"></a>Postup: Správa soukromé galerie pomocí nastavení registru
Pokud jste správce nebo vývojář rozšíření izolované prostředí, můžete řídit přístup k ovládací prvky, šablony a nástroje v Galerii Visual Studio, Ukázky Galerie nebo soukromé galerie. Chcete-li galerii zpřístupnit nebo zpřístupnit, vytvořte soubor *Pkgdef,* který popisuje upravené klíče registru a jejich hodnoty.

## <a name="manage-private-galleries"></a>Správa soukromých galerií
 Můžete vytvořit soubor *.pkgdef* pro řízení přístupu k galeriím na více počítačích. Tento soubor musí mít následující formát.

```
[$RootKey$\ExtensionManager\Repositories\{UniqueGUID}]
@={URI}  (REG_SZ)
Disabled=0 | 1 (DWORD)
Priority=0 (highest priority) ... MaxInt (lowest priority) (DWORD) (uint)
Protocol=Atom Feed|Sharepoint (REG_SZ)
DisplayName={DisplayName} (REG_SZ)
DisplayNameResourceID={ID} (REG_SZ)
DisplayNamePackageGuid={GUID} (REG_SZ)

```

 Klíč `Repositories` odkazuje na galerii, která má být povolena nebo zakázána. Galerie Visual Studia a Galerie ukázek používají následující identifikátory GUID úložiště:

- Galerie Vizuální studio : 0F45E408-7995-4375-9485-86B8DB553DC9

- Galerie vzorků : AEB9CB40-D8E6-4615-B52C-27E307F8506C

  Hodnota `Disabled` je nepovinná. Ve výchozím nastavení je galerie povolena.

  Hodnota `Priority` určuje pořadí, ve kterém jsou galerie uvedeny v dialogovém okně **Možnosti.** Visual Studio Galerie má prioritu 10 a ukázky galerie má prioritu 20. Soukromé galerie začínají na prioritě 100. Pokud má několik galerií stejnou hodnotu priority, je pořadí, ve kterém `DisplayName` se zobrazují, určeno hodnotami jejich lokalizovaných atributů.

  Hodnota `Protocol` je vyžadována pro galerie založené na atomu nebo sharepointové.

  Musí `DisplayName`být `DisplayNameResourceID` zadány buď , nebo obojí a `DisplayNamePackageGuid`. Pokud jsou zadány `DisplayNameResourceID` všechny, pak a `DisplayNamePackageGuid` pair se používá.

## <a name="disable-the-visual-studio-gallery-using-a-pkgdef-file"></a>Zakázání galerie sady Visual Studio pomocí souboru Pkgdef
 Galerii můžete zakázat v souboru *Pkgdef.* Následující položka zakáže Galerii Visual Studia:

```
[$RootKey$\ExtensionManager\Repositories\{0F45E408-7995-4375-9485-86B8DB553DC9}]
"Disabled"=dword:00000001

```

 Následující položka zakáže Galerii ukázek:

```
[$RootKey$\ExtensionManager\Repositories\{AEB9CB40-D8E6-4615-B52C-27E307F8506C}]
"Disabled"=dword:00000001

```

## <a name="see-also"></a>Viz také
- [Soukromé galerie](../extensibility/private-galleries.md)
