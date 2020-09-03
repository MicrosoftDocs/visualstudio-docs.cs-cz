---
title: Soukromé galerie | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "81444645"
---
# <a name="private-galleries"></a>Soukromé galerie
Můžete sdílet ovládací prvky, šablony a nástroje, které vyvíjíte, jejich publikováním do *soukromé Galerie* v intranetu pro vaši organizaci následujícím způsobem:

- Vytvořte informační kanál Atom (RSS) do vhodně nakonfigurovaného centrálního umístění (úložiště) na intranetu. Další informace najdete v tématu [Postup: vytvoření informačního kanálu Atom pro soukromou galerii](../extensibility/how-to-create-an-atom-feed-for-a-private-gallery.md).

- Distribuujte soubor *. pkgdef* , který popisuje soukromou galerii. Doporučujeme tuto konfiguraci správcům, kteří chtějí připojit soukromou galerii k mnoha počítačům ve stejnou dobu.

## <a name="add-a-private-gallery-to-extensions-and-updates-in-visual-studio"></a>Přidání soukromé galerie pro rozšíření a aktualizace v aplikaci Visual Studio
 Když je k dispozici soukromá galerie, můžete ji přidat do **rozšíření a aktualizací** v aplikaci Visual Studio.

 ![Přidat dialog Správce rozšíření](../extensibility/media/em_adddialog.png "EM_AddDialog")

### <a name="to-add-a-private-gallery-to-extensions-and-updates"></a>Přidání soukromé galerie pro rozšíření a aktualizace

1. Na panelu nabídek vyberte **Tools**  >  **Možnosti**nástroje.

2. V uzlu **prostředí** vyberte **rozšíření a aktualizace**.

3. Vyberte tlačítko **Přidat**.

4. Do pole **název** zadejte název soukromé galerie, například `My Gallery` .

5. Do pole **Adresa URL** zadejte adresu URL informačního kanálu Atom nebo webu služby SharePoint, který je hostitelem soukromé galerie.

    1. Pokud je hostitelem informační kanál Atom, který se připojuje k soukromé galerii, adresa URL by vypadala takto: `http://www.mywebsite/mygallery/atom.xml` .  Tato adresa URL může odkazovat na soubor nebo síťovou cestu.

    2. Pokud je hostitelem web služby SharePoint, adresa URL by vypadala takto: `http://mysharepoint/sites/mygallery/forms/AllItems.aspx` .

### <a name="manage-private-galleries"></a>Správa privátních galerií
 Správce může nastavit soukromou galerii k dispozici pro několik počítačů současně úpravou systémového registru v každém počítači. K tomu je potřeba vytvořit soubor *. pkgdef* , který popisuje nové klíče registru a jejich hodnoty.  Formát tohoto souboru je následující.

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

 Další informace najdete v tématu [Postup: Správa privátní Galerie pomocí nastavení registru](../extensibility/how-to-manage-a-private-gallery-by-using-registry-settings.md).

## <a name="install-extensions-from-a-private-gallery"></a>Instalace rozšíření z privátní Galerie
 Rozšíření sady Visual Studio můžete vyhledat a nainstalovat z privátní Galerie v **rozšířeních a aktualizacích**. Následující kroky používají soukromou galerii s názvem `My Gallery` .

 ![Správce rozšíření instalace privátní Galerie](../extensibility/media/em_.png "EM_")

### <a name="to-search-for-and-install-extensions-from-a-private-gallery"></a>Vyhledání a instalace rozšíření z privátní Galerie

1. Na řádku nabídek klikněte na **nástroje**  >  **rozšíření a aktualizace**.

2. V levém podokně vyberte **rozšíření online**a pak vyberte **Moje galerie**.

3. V pravém podokně vyberte rozšíření a pak klikněte na tlačítko **Stáhnout** .

## <a name="update-extensions-from-a-private-gallery"></a>Aktualizace rozšíření z privátní Galerie
 V případě, že jsou nové verze rozšíření sady Visual Studio publikovány v soukromé galerii, můžete aktualizovat rozšíření, která jste nainstalovali. Následující kroky používají soukromou galerii s názvem `My Repository` .

 ![Aktualizace privátní Galerie Správce rozšíření](../extensibility/media/em_update.png "EM_Update")

### <a name="to-update-an-installed-extension-from-a-private-gallery"></a>Aktualizace nainstalovaného rozšíření z privátní Galerie

1. Na řádku nabídek klikněte na **nástroje**  >  **rozšíření a aktualizace**.

2. V levém podokně vyberte **aktualizace**a pak vyberte **Moje úložiště**.

3. V pravém podokně vyberte rozšíření a pak klikněte na tlačítko **aktualizovat** .

## <a name="see-also"></a>Viz také
- [Vyhledání a používání rozšíření sady Visual Studio](../ide/finding-and-using-visual-studio-extensions.md)
- [Dodávat rozšíření sady Visual Studio](../extensibility/shipping-visual-studio-extensions.md)
