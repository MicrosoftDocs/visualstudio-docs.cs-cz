---
title: Správa soukromé Galerie pomocí nastavení registru
description: Naučte se řídit přístup k ovládacím prvkům, šablonám a nástrojům v galerii sady Visual Studio, galerii ukázek nebo soukromých galeriích.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: d15d845f07310e3efcba6f05538a2207d9c416e4
ms.sourcegitcommit: d10f37dfdba5d826e7451260c8370fd1efa2c4e4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2020
ms.locfileid: "96994003"
---
# <a name="how-to-manage-a-private-gallery-by-using-registry-settings"></a>Postupy: Správa privátní Galerie pomocí nastavení registru
Pokud jste správcem nebo vývojářem rozšíření izolovaného prostředí, můžete řídit přístup k ovládacím prvkům, šablonám a nástrojům v galerii sady Visual Studio, galerii ukázek nebo soukromých galeriích. Pokud chcete galerii zpřístupnit nebo není k dispozici, vytvořte soubor *. pkgdef* , který popisuje upravené klíče registru a jejich hodnoty.

## <a name="manage-private-galleries"></a>Správa privátních galerií
 Můžete vytvořit soubor *. pkgdef* pro řízení přístupu k galeriím na více počítačích. Tento soubor musí mít následující formát.

```
[$RootKey$\ExtensionManager\Repositories\{UniqueGUID}]
@={URI}  (REG_SZ)
Disabled=0 | 1 (DWORD)
Priority=0 (highest priority) ... MaxInt (lowest priority) (DWORD) (uint)
Protocol=Atom Feed|Sharepoint (REG_SZ)
DisplayName={DisplayName} (REG_SZ)
DisplayNameResourceID={ID} (REG_SZ)
DisplayNamePackageGuid={GUID} (REG_SZ)

```

 `Repositories`Klíč odkazuje na galerii, aby byla povolená nebo zakázaná. Galerie sady Visual Studio a Galerie ukázek používají následující identifikátory GUID úložiště:

- Galerie sady Visual Studio: 0F45E408-7995-4375-9485-86B8DB553DC9

- Galerie ukázek: AEB9CB40-D8E6-4615-B52C-27E307F8506C

  `Disabled`Hodnota je volitelná. Ve výchozím nastavení je galerie povolena.

  `Priority`Hodnota určuje pořadí, ve kterém jsou Galerie uvedeny v dialogovém okně **Možnosti** . Galerie sady Visual Studio má prioritu 10 a Galerie ukázek má prioritu 20. Soukromé Galerie začínají v prioritě 100. Pokud má několik galerií stejnou hodnotu priority, pořadí, ve kterém jsou uvedeny, je určeno hodnotami jejich lokalizovaných `DisplayName` atributů.

  `Protocol`Hodnota je vyžadována pro galerie založené na atomech nebo na SharePointu.

  `DisplayName`Musí být zadán buď, nebo obojí `DisplayNameResourceID` a `DisplayNamePackageGuid` . Pokud jsou zadány všechny, `DisplayNameResourceID` `DisplayNamePackageGuid` je použita dvojice a.

## <a name="disable-the-visual-studio-gallery-using-a-pkgdef-file"></a>Zakázání galerie sady Visual Studio pomocí souboru. pkgdef
 Galerii můžete zakázat v souboru *. pkgdef* . Následující položka zakáže galerii sady Visual Studio:

```
[$RootKey$\ExtensionManager\Repositories\{0F45E408-7995-4375-9485-86B8DB553DC9}]
"Disabled"=dword:00000001

```

 Následující položka zakáže galerii ukázek:

```
[$RootKey$\ExtensionManager\Repositories\{AEB9CB40-D8E6-4615-B52C-27E307F8506C}]
"Disabled"=dword:00000001

```

## <a name="see-also"></a>Viz také
- [Privátní galerie](../extensibility/private-galleries.md)
