---
title: Inicializace návrháře a konfigurace metadat | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- designers [Visual Studio SDK], initializing
- designers [Visual Studio SDK], configuring metadata
ms.assetid: f7fe9a7e-f669-4642-ad5d-186b2e6e6ec9
caps.latest.revision: 17
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 2dec3937616c712c56b7012949e044702e6b11f2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "65703072"
---
# <a name="designer-initialization-and-metadata-configuration"></a>Inicializace návrháře a konfigurace metadat
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Manipulace s atributy metadat a Filter přidružených k komponentě návrháře nebo návrháře poskytuje mechanismus pro aplikace pro definování, které nástroje jsou používány konkrétním návrhářem pro zpracování různých <xref:System.Type> objektů (například datových struktur, tříd nebo grafických entit), když je Návrhář dostupný a jak je rozhraní IDE sady Visual Studio nakonfigurováno pro podporu návrháře (například kategorie **panelu nástrojů** nebo karta je k dispozici).  
  
 [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)]Poskytuje několik mechanismů pro usnadnění kontroly inicializace komponenty návrháře nebo návrháře a manipulaci s metadaty pomocí VSPackage.  
  
## <a name="initializing-metadata-and-configuration-information"></a>Inicializace metadat a informací o konfiguraci  
 Vzhledem k tomu, že jsou načteny na vyžádání, nemohou být sady VSPackage načteny [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] prostředím před vytvořením instance návrháře. Sady VSPackage proto nemohou používat standardní mechanizmus pro konfiguraci návrháře nebo součásti návrháře při vytváření, což znamená zpracování <xref:System.ComponentModel.Design.IDesignerEventService.DesignerCreated> události. Místo toho VSPackage implementuje instanci <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension> rozhraní a registruje se tak, aby poskytoval vlastní nastavení, označované jako rozšíření návrhová plocha.  
  
### <a name="customizing-initialization"></a>Přizpůsobení inicializace  
 Přizpůsobení návrháře, komponenty nebo návrhové plochy zahrnuje:  
  
1. Úprava metadat návrháře a efektivní změna způsobu, jakým <xref:System.Type> je určitý nebo převedený.  
  
     To se obvykle provádí pomocí <xref:System.Drawing.Design.UITypeEditor> <xref:System.ComponentModel.TypeConverter> mechanismů nebo.  
  
     Například při <xref:System.Windows.Forms> inicializaci návrháře založeného na [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] prostředí upraví prostředí <xref:System.Drawing.Design.UITypeEditor> pro <xref:System.Web.UI.WebControls.Image> objekty používané v Návrháři k použití Správce prostředků k získání rastrových obrázků namísto systému souborů.  
  
2. Integrace s prostředím například po přihlášení k odběru událostí nebo získání informací o konfiguraci projektu. Můžete získat informace o konfiguraci projektu a přihlásit se k odběru událostí získáním <xref:System.ComponentModel.Design.ITypeResolutionService> rozhraní.  
  
3. Úprava uživatelského prostředí aktivací příslušných kategorií **nástrojů** nebo omezením použitelnosti návrháře použitím instance <xref:System.ComponentModel.ToolboxItemFilterAttribute> třídy pro návrháře.  
  
### <a name="designer-initialization-by-a-vspackage"></a>Inicializace návrháře pomocí VSPackage  
 VSPackage by měl zvládnout inicializaci návrháře:  
  
1. Vytvoření objektu, který implementuje <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension> třídu.  
  
   > [!NOTE]
   > <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension>Třída by nikdy neměla být implementovaná u stejného objektu jako <xref:Microsoft.VisualStudio.Shell.Package> Třída.  
  
2. Zaregistrujte třídu implementující <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension> jako podporu rozšíření návrháře VSPackage pomocí instancí  <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtensionAttribute> <xref:Microsoft.VisualStudio.Shell.ProvideObjectAttribute> a <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute> na třídu, která poskytuje implementaci rozhraní VSPackage <xref:Microsoft.VisualStudio.Shell.Package> .  
  
   Při každém vytvoření návrháře nebo komponenty návrháře [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] prostředí:  
  
3. Přistupuje ke každému zaregistrovanému poskytovateli rozšíření návrhová plocha.  
  
4. Vytvoří instanci a inicializuje instanci každého objektu poskytovatele rozšíření pro návrhovou plochu. <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension>  
  
5. Volá metodu nebo metodu poskytovatele rozšíření pro návrhovou plochu <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension.OnDesignerCreated%2A> <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension.OnComponentCreated%2A> (podle potřeby).  
  
   Při implementaci <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension> objektu jako člena sady VSPackage je důležité pochopit, že:  
  
6. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]Prostředí neposkytuje žádnou kontrolu nad tím, jaká metadata nebo jiná nastavení konfigurace konkrétní `DesignSurfaceExtension` poskytovatel mění. Je možné, že dva nebo více `DesignSurfaceExtension` zprostředkovatelů mění stejnou funkci návrháře v konfliktních způsobech s konečnou úpravou. Nejedná se o neurčitou úpravu, kterou poslední změnu používá.  
  
7. Je možné explicitně omezit implementaci <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension> objektu na konkrétní návrháře tím, že použijete instance <xref:System.ComponentModel.ToolboxItemFilterAttribute> pro tuto implementaci. Další informace o filtrování položek **panelu nástrojů** naleznete v tématu <xref:System.ComponentModel.ToolboxItemFilterAttribute> a <xref:System.ComponentModel.ToolboxItemFilterType> .  
  
## <a name="additional-metadata-provisioning"></a>Další zřizování metadat  
 VSPackage může změnit konfiguraci součásti návrháře nebo návrháře jinou než v době návrhu.  
  
 <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute>Třídu lze použít programově nebo ji použít pro VSPackage, který poskytuje návrháře.  
  
 Instance <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute> třídy se používá pro úpravu metadat komponent vytvořených na návrhové ploše. Například jedna by mohla nahradit výchozí prohlížeč vlastností používané <xref:System.Windows.Forms.CommonDialog> objekty, a to s využitím prohlížeče vlastních vlastností.  
  
 Změny, které poskytuje instance <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute> použité pro implementaci sady VSPackage, <xref:Microsoft.VisualStudio.Shell.Package> můžou mít jeden ze dvou oborů:  
  
- Global – pro všechny nové instance dané komponenty  
  
- Místní – týká se jenom instance komponenty vytvořené na návrhové ploše, kterou poskytuje aktuální VSPackage.  
  
  `IsGlobal`Vlastnost <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute> instance použitá pro implementaci sady VSPackage <xref:Microsoft.VisualStudio.Shell.Package> tohoto oboru.  
  
  Použití atributu na implementaci <xref:Microsoft.VisualStudio.Shell.Package> s <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute.IsGlobal%2A> vlastností <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute> objektu nastavenou na hodnotu, jak je uvedeno `true` níže, změní prohlížeč pro celé [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] prostředí:  
  
  `[ProvideDesignerMetadata(typeof(Color), typeof(CustomBrowser),`   `IsGlobal=true`  `)]`  
  
  `internal class MyPackage : Package {}`  
  
  Pokud byl globální příznak nastaven na `false` , je změna metadat místní pro aktuální Návrhář podporovaný aktuálním rozhraním VSPackage:  
  
  `[ProvideDesignerMetadata(typeof(Color), typeof(CustomBrowser),`   `IsGlobal=false`  `)]`  
  
  `internal class MyPackage : Package {}`  
  
> [!NOTE]
> V současné době návrhová plocha podporuje pouze vytváření komponent, a proto může mít místní metadata pouze součásti. V předchozím příkladu jsme se pokoušeli změnit vlastnost, jako je například `Color` vlastnost objektu. Pokud `false` byla předána pro globální příznak, `CustomBrowser` by se nikdy nezobrazila, protože Návrhář nikdy nevytvořil instanci `Color` . Nastavení globálního příznaku na `false` hodnotu je užitečné pro součásti, jako jsou ovládací prvky, časovače a dialogová okna.  
  
## <a name="see-also"></a>Viz také  
 <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension>   
 <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtensionAttribute>   
 <xref:System.ComponentModel.ToolboxItemFilterType>   
 [Rozšíření podpory během návrhu](https://msdn.microsoft.com/library/d6ac8a6a-42fd-4bc8-bf33-b212811297e2)
