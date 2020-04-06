---
title: Inicializace návrháře a konfigurace metadat | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- designers [Visual Studio SDK], initializing
- designers [Visual Studio SDK], configuring metadata
ms.assetid: f7fe9a7e-f669-4642-ad5d-186b2e6e6ec9
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e876dd9e6fa95bbe180d1737bc8c4911f16e1e9a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712213"
---
# <a name="designer-initialization-and-metadata-configuration"></a>Inicializace návrháře a konfigurace metadat

Manipulace s metadaty a atributy filtru přidružené k návrháři nebo součásti návrháře poskytuje mechanismus <xref:System.Type> pro aplikace definovat, které nástroje jsou používány konkrétní návrhář pro zpracování různých objektů (například datové struktury, třídy nebo grafické entity), když je k dispozici návrháře a jak je rozhraní Visual Studio IDE nakonfigurovánpro podporu návrháře (například které panel **nástrojů** kategorie nebo karta je k dispozici).

Poskytuje [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] několik mechanismů pro usnadnění řízení inicializace součásti návrháře nebo návrháře a manipulace s jeho metadaty vbalíček VSPackage.

## <a name="initialize-metadata-and-configuration-information"></a>Inicializovat metadata a informace o konfiguraci
 Vzhledem k tomu, že jsou načteny na vyžádání, VSPackages pravděpodobně nebyly načteny prostředí sady Visual Studio před vytvoření mnoství návrháře. Proto VSPackages nelze použít standardní mechanismus pro konfiguraci návrháře nebo návrháře součást při vytváření, což je zpracování <xref:System.ComponentModel.Design.IDesignerEventService.DesignerCreated> události. Místo toho VSPackage implementuje <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension> instanci rozhraní a registruje sám poskytovat vlastní nastavení, označované jako rozšíření návrhu povrchu.

### <a name="customize-initialization"></a>Přizpůsobení inicializace

Přizpůsobení návrháře, součásti nebo povrchu návrháře zahrnuje:

1. Úprava metadat návrháře a efektivní změna <xref:System.Type> způsobu přístupu k určité změně nebo převodu.

    To se obvykle provádí <xref:System.Drawing.Design.UITypeEditor> <xref:System.ComponentModel.TypeConverter> prostřednictvím nebo mechanismy.

    Například při <xref:System.Windows.Forms>inicializovány návrháři založené na- Nastavení <xref:System.Drawing.Design.UITypeEditor> <xref:System.Web.UI.WebControls.Image> aplikace Visual Studio upraví pro objekty používané s návrhářem použít správce prostředků k získání bitmap spíše než systém souborů.

2. Integrace s prostředím, například přihlášením se k odběru událostí nebo získáním informací o konfiguraci projektu. Informace o konfiguraci projektu a přihlášení <xref:System.ComponentModel.Design.ITypeResolutionService> k odběru událostí získáním rozhraní.

3. Změna uživatelského prostředí aktivací příslušných kategorií **panelu nástrojů** nebo omezením použitelnosti návrháře použitím instance <xref:System.ComponentModel.ToolboxItemFilterAttribute> třídy na návrháře.

### <a name="designer-initialization-by-a-vspackage"></a>Inicializace návrháře balíčkem VSPackage

VSPackage by měl zpracovat inicializaci návrháře:

1. Vytvoření objektu implementujícího třídu. <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension>

   > [!NOTE]
   > Třída <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension> by nikdy být implementována <xref:Microsoft.VisualStudio.Shell.Package> na stejný objekt jako třída.

2. Registrace třídy, která <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension> implementuje jako poskytování podpory pro rozšíření návrháře VSPackage. Zaregistrujte třídu použitím <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtensionAttribute>instancí , <xref:Microsoft.VisualStudio.Shell.ProvideObjectAttribute>a <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute> na třídu, která <xref:Microsoft.VisualStudio.Shell.Package>poskytuje implementaci VSPackage .

Při každém vytvoření součásti návrháře nebo návrháře prostředí Visual Studio:

- Přistupuje ke každému registrovanému zprostředkovateli rozšíření plochy návrhu.

- Instanci a inicializuje instanci každého <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension> poskytovatele rozšíření plochy návrhu objektu.

- Volá každý návrh rozšíření <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension.OnDesignerCreated%2A> povrchu <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension.OnComponentCreated%2A> metody nebo metody (podle potřeby).

Při implementaci <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension> objektu jako člen VSPackage, je důležité si uvědomit, že:

- Prostředí sady Visual Studio neposkytuje žádnou kontrolu nad tím, jaká metadata nebo jiná nastavení konfigurace konkrétního `DesignSurfaceExtension` zprostředkovatele upravuje. Je možné pro dva `DesignSurfaceExtension` nebo více zprostředkovatelů úpravy stejné funkce návrháře v konfliktní způsoby, s konečnou změnou je definitivní. Je neurčitý, která změna je naposledy použita.

- Je možné explicitně omezit implementaci <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension> objektu na konkrétní návrháře <xref:System.ComponentModel.ToolboxItemFilterAttribute> použitím instance této implementace. Další informace o filtrování položek **panelu nástrojů** naleznete v tématu <xref:System.ComponentModel.ToolboxItemFilterAttribute> a . <xref:System.ComponentModel.ToolboxItemFilterType>

## <a name="additional-metadata-provisioning"></a>Další zřizování metadat

VSPackage můžete změnit konfiguraci návrháře nebo návrháře součásti než v době návrhu.

Třídu <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute> lze použít programově nebo použít na VSPackage, který poskytuje návrháře.

Instance třídy <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute> se používá k úpravě metadat součástí vytvořených na návrhové ploše. Například jeden by mohl nahradit výchozí <xref:System.Windows.Forms.CommonDialog> prohlížeč vlastností používaný objekty s vlastní vlastnostprohlížeče.

Změny poskytované instance <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute> použít v implementaci VSPackage <xref:Microsoft.VisualStudio.Shell.Package> může mít jeden ze dvou oborů:

- Globální – pro všechny nové instance dané součásti

- Local -- se vztahuje pouze na instanci součásti vytvořené na návrhové ploše poskytované aktuální VSPackage.

Vlastnost `IsGlobal` <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute> instance použitá pro implementaci VSPackage <xref:Microsoft.VisualStudio.Shell.Package> určuje tento obor.

Použití atributu na <xref:Microsoft.VisualStudio.Shell.Package> implementaci <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute.IsGlobal%2A> s vlastností objektu <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute> nastaveného na , jak je `true`uvedeno níže, změní prohlížeč pro celé prostředí sady Visual Studio:

`[ProvideDesignerMetadata(typeof(Color), typeof(CustomBrowser),`   `IsGlobal=true`  `)]`

`internal class MyPackage : Package {}`

Pokud byl globální příznak `false`nastaven na , je změna metadat místní pro aktuální návrhářpodporovaný aktuálním balíčkem VSPackage:

`[ProvideDesignerMetadata(typeof(Color), typeof(CustomBrowser),`   `IsGlobal=false`  `)]`

`internal class MyPackage : Package {}`

> [!NOTE]
> Návrhová plocha podporuje pouze vytváření součástí, a proto pouze součásti mohou mít místní metadata. Ve výše uvedeném příkladu jsme se pokoušeli `Color` změnit vlastnost, například vlastnost objektu. Pokud `false` byl předán v pro `CustomBrowser` globální příznak, by se nikdy `Color`nezobrazí, protože návrhář nikdy ve skutečnosti vytvoří instanci . Nastavení globálního příznaku na `false` je užitečné pro součásti, jako jsou ovládací prvky, časovače a dialogová okna.

## <a name="see-also"></a>Viz také

- <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension>
- <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtensionAttribute>
- <xref:System.ComponentModel.ToolboxItemFilterType>
- [Prodloužení podpory návrhu](https://msdn.microsoft.com/Library/d6ac8a6a-42fd-4bc8-bf33-b212811297e2)
