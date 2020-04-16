---
title: Soukromé galerie | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSIX galleries, private
- private galleries, VSIX
ms.assetid: b6b3dee7-91c5-4556-9f69-0d56b675e83b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: afd1d79d7f1846e60386d2a9478466bf7eae72e4
ms.sourcegitcommit: 7b60e81414a82c6d34f6de1a1f56115c9cd26943
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/16/2020
ms.locfileid: "81444645"
---
# <a name="private-galleries"></a>Soukromé galerie
Ovládací prvky, šablony a nástroje, které vyvíjíte, můžete sdílet tak, že je zveřejníte v *soukromé galerii* v síti intranet pro vaši organizaci, a to následovně:

- Vytvořte informační kanál RsS (Atom) do vhodně nakonfigurovaného centrálního umístění (úložiště) v intranetu. Další informace naleznete v [tématu How to: Create atom feed for a private gallery](../extensibility/how-to-create-an-atom-feed-for-a-private-gallery.md).

- Rozdejte soubor *.pkgdef,* který popisuje soukromou galerii. Tuto konfiguraci doporučujeme správcům, kteří chtějí současně připojit soukromou galerii k mnoha počítačům.

## <a name="add-a-private-gallery-to-extensions-and-updates-in-visual-studio"></a>Přidání soukromé galerie k rozšířením a aktualizacím v sadě Visual Studio
 Když je k dispozici soukromá galerie, můžete ji přidat do **rozšíření a aktualizace** v sadě Visual Studio.

 ![Dialogové okno Přidat Správce rozšíření](../extensibility/media/em_adddialog.png "EM_AddDialog")

### <a name="to-add-a-private-gallery-to-extensions-and-updates"></a>Přidání soukromé galerie do rozšíření a aktualizací

1. Na řádku nabídek zvolte**Možnosti** **nástrojů** > .

2. V uzlu **Prostředí** vyberte **Rozšíření a aktualizace**.

3. Vyberte tlačítko **Přidat**.

4. Do pole **Název** zadejte název soukromé galerie, `My Gallery`například .

5. Do pole **URL** zadejte adresu URL informačního kanálu Atom nebo sharepointového webu, který je hostitelem soukromé galerie.

    1. Pokud je hostitelem informační kanál Atom, který se připojuje k `http://www.mywebsite/mygallery/atom.xml`soukromé galerii, adresa URL by se podobala této adrese: .  Tato adresa URL může odkazovat na soubor nebo síťovou cestu.

    2. Pokud je hostitelem sharepointový web, bude `http://mysharepoint/sites/mygallery/forms/AllItems.aspx`adresa URL vypadat podobně jako tato: .

### <a name="manage-private-galleries"></a>Správa soukromých galerií
 Správce může zpřístupnit soukromou galerii několika počítačům současně úpravou systémového registru v každém počítači. Chcete-li to provést, vytvořte soubor *.pkgdef,* který popisuje nové klíče registru a jejich hodnoty.  Formát tohoto souboru je následující.

```
[$RootKey$\ExtensionManager\Repositories\{UniqueGUID}]
@={URI}  (REG_SZ)
Disabled=0 | 1 (DWORD)
Priority=0 (highest priority) ... MaxInt (lowest priority) (DWORD) (uint)
Protocol=Atom|Sharepoint (REG_SZ)
DisplayName={DisplayName} (REG_SZ)
DisplayNameResourceID={ID} (REG_SZ)
DisplayNamePackageGuid={GUID} (REG_SZ)

```

 Další informace naleznete v [tématu Postup: Správa soukromé galerie pomocí nastavení registru](../extensibility/how-to-manage-a-private-gallery-by-using-registry-settings.md).

## <a name="install-extensions-from-a-private-gallery"></a>Instalace rozšíření ze soukromé galerie
 Rozšíření sady Visual Studio můžete vyhledat a nainstalovat ze soukromé galerie v **části Rozšíření a aktualizace**. Následující kroky používají soukromou `My Gallery`galerii s názvem .

 ![Správce rozšíření instaluje soukromou galerii](../extensibility/media/em_.png "EM_")

### <a name="to-search-for-and-install-extensions-from-a-private-gallery"></a>Vyhledání a instalace rozšíření ze soukromé galerie

1. Na řádku nabídek zvolte**Rozšíření a aktualizace** **nástrojů** > .

2. V levém podokně vyberte **Online rozšíření**a pak vyberte **Moje galerie**.

3. V pravém podokně vyberte rozšíření a pak zvolte tlačítko **Stáhnout.**

## <a name="update-extensions-from-a-private-gallery"></a>Aktualizace rozšíření ze soukromé galerie
 Jako nové verze rozšíření Sady Visual Studio jsou zaúčtovány v soukromé galerii, můžete aktualizovat rozšíření, které jste nainstalovali. Následující kroky používají soukromou `My Repository`galerii s názvem .

 ![Aktualizace galerie správce rozšíření](../extensibility/media/em_update.png "EM_Update")

### <a name="to-update-an-installed-extension-from-a-private-gallery"></a>Aktualizace nainstalovaného rozšíření ze soukromé galerie

1. Na řádku nabídek zvolte**Rozšíření a aktualizace** **nástrojů** > .

2. V levém podokně vyberte **Aktualizace**a pak vyberte **Moje úložiště**.

3. V pravém podokně vyberte rozšíření a pak zvolte tlačítko **Aktualizovat.**

## <a name="see-also"></a>Viz také
- [Vyhledání a používání rozšíření sady Visual Studio](../ide/finding-and-using-visual-studio-extensions.md)
- [Rozšíření aplikace Visual Studio](../extensibility/shipping-visual-studio-extensions.md)
