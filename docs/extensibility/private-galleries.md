---
title: Privátní Galerie | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSIX galleries, private
- private galleries, VSIX
ms.assetid: b6b3dee7-91c5-4556-9f69-0d56b675e83b
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: e91b3ecec969ab6a717598d8dfb77e674890216a
ms.sourcegitcommit: 06db1892fff22572f0b0a11994dc547c2b7e2a48
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/08/2018
ms.locfileid: "39638580"
---
# <a name="private-galleries"></a>Privátní Galerie
Můžete sdílet ovládací prvky, šablony a nástroje, které vyvíjíte jejich zveřejněním *privátní Galerie* v síti intranet pro vaši organizaci, a to následujícím způsobem:  
  
-   Vytvořte kanál Atom (RSS) do centrálního umístění vhodně nakonfigurovaná (úložiště) na vašem intranetu. Další informace najdete v tématu [postupy: vytvoření Atom pro privátní galerii](../extensibility/how-to-create-an-atom-feed-for-a-private-gallery.md).  
  
-   Distribuce *.pkgdef* soubor, který popisuje privátní galerie. Doporučujeme tuto konfiguraci pro správce, kteří se chcete připojit soukromou galerii mnoho počítačů současně.  
  
## <a name="add-a-private-gallery-to-extensions-and-updates-in-visual-studio"></a>Přidejte privátní galerii rozšíření a aktualizace v sadě Visual Studio  
 Privátní Galerie je k dispozici, můžete přidávat na **rozšíření a aktualizace** v sadě Visual Studio.  
  
 ![Dialogové okno pro přidání správce rozšíření](../extensibility/media/em_adddialog.png "EM_AddDialog")  
  
### <a name="to-add-a-private-gallery-to-extensions-and-updates"></a>Chcete-li přidat soukromou galerii rozšíření a aktualizace  
  
1.  V panelu nabídky zvolte **nástroje** > **možnosti**.  
  
2.  V **prostředí** uzlu, vyberte **rozšíření a aktualizace**.  
  
3.  Zvolte **přidat** tlačítko.  
  
4.  V **název** pole, zadejte název pro privátní galerii, například `My Gallery`.  
  
5.  V **URL** zadejte adresu URL informačního kanálu Atom nebo webu služby SharePoint, který je hostitelem privátní galerie.  
  
    1.  Pokud je hostitel informačního kanálu Atom, která se připojuje k privátní galerie, adresa URL by vypadat podobně jako tato: http://www.mywebsite/mygallery/atom.xml.  Tato adresa URL může odkazovat na soubor nebo síťovou cestu.  
  
    2.  Pokud hostitel je web služby SharePoint, adresa URL by vypadat podobně jako tato: http://mysharepoint/sites/mygallery/forms/AllItems.aspx.  
  
### <a name="manage-private-galleries"></a>Správa privátní Galerie  
 Správce může zpřístupnit soukromou galerii několik počítačů ve stejnou dobu úpravou registru systému na každém počítači. Chcete-li to provést, vytvořte *.pkgdef* soubor, který popisuje nové klíče registru a jejich hodnoty.  Formát tohoto souboru je následující.  
  
```  
[$RootKey$\ExtensionManager\Repositories\{UniqueGUID}]  
@={URI}  (REG_SZ)  
Disabled=0 | 1 (DWORD)  
Priority=0 (highest priority) ... MaxInt (lowest priority) (DWORD) (uint)  
Protocol=Atom|Sharepoint (REG_SZ)  
DisplayName={DisplayName} (REG_SZ)  
DisplayNameResourceID={ID} (REG_SZ)  
DisplayNamePackageGuid={GUID} (REG_SZ)  
  
```  
  
 Další informace najdete v tématu [postupy: Správa privátní galerie s použitím nastavení registru](../extensibility/how-to-manage-a-private-gallery-by-using-registry-settings.md).  
  
## <a name="install-extensions-from-a-private-gallery"></a>Nainstalovat rozšíření z privátní Galerie  
 Můžete vyhledat a nainstalovat rozšíření sady Visual Studio z privátní Galerie v **rozšíření a aktualizace**. Následující kroky používají privátní galerie s názvem `My Gallery`.  
  
 ![Správce rozšíření pro instalaci privátní Galerie](../extensibility/media/em_.png "EM_")  
  
### <a name="to-search-for-and-install-extensions-from-a-private-gallery"></a>K vyhledání a instalace rozšíření z privátní Galerie  
  
1.  V panelu nabídky zvolte **nástroje** > **rozšíření a aktualizace**.  
  
2.  V levém podokně vyberte **Online rozšíření**a pak vyberte **Moje galerie**.  
  
3.  V pravém podokně vyberte rozšíření a klikněte na tlačítko **Stáhnout** tlačítko.  
  
## <a name="update-extensions-from-a-private-gallery"></a>Aktualizace rozšíření z privátní Galerie  
 Jako nová verze rozšíření sady Visual Studio jsme zveřejnili v privátní galerii, můžete aktualizovat rozšíření, které jste nainstalovali. Následující kroky používají privátní galerie s názvem `My Repository`.  
  
 ![Aktualizace rozšíření správce privátní Galerie](../extensibility/media/em_update.png "EM_Update")  
  
### <a name="to-update-an-installed-extension-from-a-private-gallery"></a>K aktualizaci nainstalovaného rozšíření z privátní Galerie  
  
1.  V panelu nabídky zvolte **nástroje** > **rozšíření a aktualizace**.  
  
2.  V levém podokně vyberte **aktualizace**a pak vyberte **Moje úložiště**.  
  
3.  V pravém podokně vyberte rozšíření a klikněte na tlačítko **aktualizace** tlačítko.  
  
## <a name="see-also"></a>Viz také:  
 [Vyhledání a používání rozšíření sady Visual Studio](../ide/finding-and-using-visual-studio-extensions.md)   
 [Dodávejte rozšíření sady Visual Studio](../extensibility/shipping-visual-studio-extensions.md)