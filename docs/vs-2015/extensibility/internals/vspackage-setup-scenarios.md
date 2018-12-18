---
title: Scénáře instalace balíčku VSPackage | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- VSPackages, deployment considerations
ms.assetid: d2928498-f27c-46b4-a9cd-cba41fd85a10
caps.latest.revision: 22
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 34181e5b03b29662188e368561b0f43049629ec1
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51788547"
---
# <a name="vspackage-setup-scenarios"></a>Scénáře instalace balíčku VSPackage
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Je důležité při návrhu balíčku VSPackage instalační program pro flexibilitu. Například možná budete muset v budoucnu vydání opravy zabezpečení, nebo můžete změnit strategii, která vyžaduje podpora důkladné verzí vedle sebe.  
  
 V [podporuje více verzí sady Visual Studio](../../extensibility/supporting-multiple-versions-of-visual-studio.md), si můžete přečíst o, jaké výhody a problémy podpory – souběžnými instalacemi sady [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] s sdílené nebo vedle sebe instalací vašeho balíčku VSPackage. Stručně řečeno, rozšíření VSPackages vedle sebe získáte největší flexibilitu pro podporu nových funkcí služby [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].  
  
 Scénáře popsané v tomto tématu nejsou vaší jedinou možností, ale jsou uvedeny jako doporučené osvědčené postupy.  
  
## <a name="components-privacy-and-sharing"></a>Komponenty, ochrany osobních údajů a sdílení  
  
##### <a name="make-your-components-independent"></a>Aby vaše komponenty nezávislý  
 Po identifikaci a naplnit součásti, přiřadit `GUID`a nasadíte komponentu, nebudete moct změnit jeho složení. Pokud změníte složení komponenty výsledné komponenty musí být nové komponenty s novou `GUID`. Zadaný tyto skutečnosti, je tím, že každá komponenta nezávislá, běžných jednotka poskytnuté nejvyšší flexibilitu správy verzí. Další informace o pravidlech, kterými se řídí součásti najdete v tématu [Změna kódu komponent](http://msdn.microsoft.com/library/aa367849\(VS.85\).aspx) a [co se stane, když je součástí pravidla jsou rozdělená?](http://msdn.microsoft.com/library/aa372795\(VS.85\).aspx).  
  
##### <a name="do-not-mix-shared-and-private-resources-in-a-component"></a>Nekombinujte sdílené a privátní zdroje v součásti  
 Počítání odkazů probíhá na úrovni součásti. V důsledku toho kombinování sdílené a privátní zdroje v jedné součásti znemožňuje aktualizovat soukromým prostředkům, jako je spustitelný soubor, aniž byste museli také přepsat sdílené prostředky. V tomto scénáři vytváří problémům se zpětnou kompatibilitou a brání vytváření funkce vedle sebe.  
  
 Například hodnoty registru použije k registraci vašeho balíčku VSPackage pomocí [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)] by měl být udržovány v komponentě odděleně od použitý k registraci vašeho balíčku VSPackage pomocí [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]. Sdílené soubory nebo hodnoty registru přejděte v ještě jiné součásti.  
  
## <a name="scenario-1-shared-vspackage"></a>Scénář 1: Sdílený VSPackage  
 V tomto scénáři sdílené VSPackage (jeden binární soubor, který podporuje více verzí [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]) je součástí balíčku Instalační služby systému Windows. Registrace s jednotlivými verzemi sady [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] řídí uživatelsky volitelných funkcí. To také znamená, že při zařazena do oddělené funkce, jednotlivé komponenty můžete vybrat jednotlivě pro instalaci nebo odinstalaci, umožňuje uživateli kontrolu nad integrace sady VSPackage v různých verzích [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]. (Viz [funkce Instalační služby systému Windows](http://msdn.microsoft.com/library/aa372840\(VS.85\).aspx) Další informace o použití funkcí v balíčky Instalační služby systému Windows.)  
  
 ![Obrázek VSPackage sdílené VS](../../extensibility/internals/media/vs-sharedpackage.gif "VS_SharedPackage")  
Sdílené instalačního programu balíčku VSPackage  
  
 Jak je znázorněno na obrázku, sdílené komponenty jsou součástí Feat_Common funkci, která je vždy nainstalován. Tím, že funkce Feat_VS2002 a Feat_VS2003 viditelné, uživatelé si můžou vybrat během instalace do verzí [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] chtějí balíčku VSPackage pro integraci. Uživatele můžete také používat režim údržby Instalační služby systému Windows k přidání nebo odebrání funkcí, které v tomto případě přidává a odebírá VSPackage registrační informace z různých verzí [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].  
  
> [!NOTE]
>  Sloupec zobrazení funkce nastavení na hodnotu 0 skrývá ho. Hodnota sloupec nízké úrovně, jako je například 1, zajistí, že bude vždy nainstalován. Další informace najdete v tématu [INSTALLLEVEL vlastnost](http://msdn.microsoft.com/library/aa369536\(VS.85\).aspx) a [tabulka funkcí](http://msdn.microsoft.com/library/aa368585.aspx).  
  
## <a name="scenario-2-shared-vspackage-update"></a>Scénář 2: Sdílet aktualizace balíčku VSPackage  
 V tomto scénáři je dodáván aktualizovanou verzi instalačního programu balíčku VSPackage ve scénáři 1. Pro účely diskuse, tato aktualizace přidává podporu pro [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)], ale mohou být také jednodušší zabezpečení opravy nebo oprava chyby aktualizace service pack. Pravidla Instalační služby Windows pro instalaci součásti novější vyžadují, nejsou znovu zkopírovány beze změny součástí už v systému. V takovém případě systém s verze 1.0 již přepsat aktualizované součásti Comp_MyVSPackage.dll a umožněte uživatelům si vybrat, chcete-li přidat novou funkci Feat_VS2005 s jeho součásti Comp_VS2005_Reg.  
  
> [!CAUTION]
>  Vždy, když je VSPackage sdílen mezi více verzí [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)], je nezbytné, že novějšími verzemi sady VSPackage zachování zpětné kompatibility se staršími verzemi sady [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]. Pokud nejde udržovat zpětnou kompatibilitu, je nutné použít vedle sebe, privátní balíčky VSPackages. Další informace najdete v tématu [podporuje více verzí sady Visual Studio](../../extensibility/supporting-multiple-versions-of-visual-studio.md).  
  
 ![Obrázek balíčku aktualizace VS sdílené VS](../../extensibility/internals/media/vs-sharedpackageupdate.gif "VS_SharedPackageUpdate")  
Sdílené instalačního programu aktualizace balíčku VSPackage  
  
 Tento scénář představuje nový instalační program balíčku VSPackage využití výhod podpory Windows instalačního programu pro dílčí upgrady. Uživatelé jednoduše nainstalovat verze 1.1 a upgradu verze 1.0. Není však nutné mít verzi 1.0 v systému. Stejný instalační program nainstaluje verze 1.1 v systému bez verze 1.0. Výhodou zadejte menší upgrady tímto způsobem je, že není nutné kvůli tomu provádět práci vývoj upgrade instalačního programu a instalační program, který plně produktu. Jeden instalační program nemá obě úlohy. Opravy zabezpečení nebo service pack může místo toho využijte výhod oprav Instalační služby systému Windows. Další informace najdete v tématu [opravy a upgrady](http://msdn.microsoft.com/library/aa370579\(VS.85\).aspx).  
  
## <a name="scenario-3-side-by-side-vspackage"></a>Scénář 3: VSPackage vedle sebe  
 Tento scénář nabízí dva instalační programy VSPackage – jeden pro každou verzi sady Visual Studio .NET 2003 a [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]. Každý instalační program nainstaluje vedle sebe nebo privátní, balíčku VSPackage (ten, který je speciálně vytvořené a nainstalovaných pro konkrétní verzi [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]). Každý balíček VSPackage správy kódu je ve vlastní komponenty. V důsledku toho každá lze jednotlivě udržovat s opravami nebo údržby uvolní. Vzhledem k tomu, že knihovna DLL balíčku VSPackage je nyní specifické pro verzi, je bezpečné registrační informace patří pod stejnou komponentou jako knihovnu DLL.  
  
 ![Na straně VS&#45;podle&#45;grafiky VS balíčku na straně](../../extensibility/internals/media/vs-sbys-package.gif "VS_SbyS_Package")  
Instalační program balíčku VSPackage vedle sebe  
  
 Každý instalační služba také zahrnuje kód, který je sdílen mezi dva instalační programy. Pokud instalaci sdílený kód do společného umístění instalace oba soubory .msi nainstaluje sdílený kód pouze jednou. Druhý instalační program právě zvýší počet odkazů na komponentu. Počet odkazů se zajistí, že pokud jeden z rozšíření VSPackages se odinstaluje, sdílený kód zůstane pro sady VSPackage. Po odinstalaci je také druhá VSPackage, sdílený kód se odeberou.  
  
## <a name="scenario-4-side-by-side-vspackage-update"></a>Scénář 4: Aktualizace balíčku VSPackage vedle sebe  
 V tomto scénáři vaše VSPackage pro [!INCLUDE[vsprvslong](../../includes/vsprvslong-md.md)] utrpělo z zabezpečení ohrožení zabezpečení a potřebujete vydat aktualizaci. Jako ve scénáři 2 můžete vytvořit nový soubor MSI, který aktualizuje existující instalace zahrnovat opravy zabezpečení, jakož i nasadit nové instalace s opravou zabezpečení již v místě.  
  
 V tomto případě je sady VSPackage spravované VSPackage nainstalované v globální mezipaměti sestavení (GAC). Když znovu vytvoříte tak, aby obsahovala opravy zabezpečení, je nutné změnit revize číselnou část čísla verze sestavení. Informace o registraci nové číslo verze sestavení přepíše předchozí verze, což způsobí [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] načíst oprava sestavení.  
  
 ![Na straně VS&#45;podle&#45;aktualizace balíčku VS straně obrázek](../../extensibility/internals/media/vs-sbys-packageupdate.gif "VS_SbyS_PackageUpdate")  
Instalační program aktualizace balíčku VSPackage vedle sebe  
  
 **Poznámka:** Další informace o nasazení sestavení vedle sebe, naleznete v tématu [zjednodušuje nasazení a řešení knihovny DLL a tím zlepšují s rozhraním .NET Framework](http://msdn.microsoft.com/library/ms973843.aspx).  
  
## <a name="see-also"></a>Viz také  
 [Instalační služby systému Windows](http://msdn.microsoft.com/library/cc185688\(VS.85\).aspx)   
 [Podpora více verzí sady Visual Studio](../../extensibility/supporting-multiple-versions-of-visual-studio.md)

