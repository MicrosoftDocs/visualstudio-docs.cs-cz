---
title: Scénáře instalace VSPackage | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, deployment considerations
ms.assetid: d2928498-f27c-46b4-a9cd-cba41fd85a10
caps.latest.revision: 22
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a09b794a6cd81966df45a1b30182040d7ab9335e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "65696747"
---
# <a name="vspackage-setup-scenarios"></a>Scénáře instalace balíčku VSPackage
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Je důležité navrhnout instalační program VSPackage pro flexibilitu. Například může být potřeba opravit opravu zabezpečení v budoucnu nebo můžete změnit obchodní strategii, která vyžaduje důkladnou podporu souběžného používání verzí.  
  
 V [podpoře více verzí sady Visual Studio](../../extensibility/supporting-multiple-versions-of-visual-studio.md)si můžete přečíst informace o výhodách a potížích s podporou souběžných instalací [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] s buď sdílených nebo souběžnými instalacemi sady VSPackage. V krátkých a souběžných rozhraních VSPackage získáte největší flexibilitu při podpoře nových funkcí nástroje [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] .  
  
 Scénáře popsané v tomto tématu nejsou vaší jedinou možností, ale zobrazují se jako doporučené osvědčené postupy.  
  
## <a name="components-privacy-and-sharing"></a>Komponenty, ochrana osobních údajů a sdílení  
  
##### <a name="make-your-components-independent"></a>Nezávislé na komponentách  
 Jakmile identifikujete a naplníte komponentu, přiřadíte a `GUID` nasadíte komponentu, nemůžete změnit její složení. Pokud změníte kompozici komponenty, výsledná součást musí být novou součástí s novým `GUID` . Vzhledem k těmto skutečnostem je flexibilita nejvyšší verze zajištěna tím, že se každá komponenta nezávislá, samostatná jednotka. Další informace o pravidlech, kterými se řídí komponenty, naleznete v tématu [Změna kódu komponenty](https://msdn.microsoft.com/library/aa367849\(VS.85\).aspx) a [co se stane, pokud jsou pravidla komponent poškozena?](https://msdn.microsoft.com/library/aa372795\(VS.85\).aspx).  
  
##### <a name="do-not-mix-shared-and-private-resources-in-a-component"></a>Nemíchat sdílené a soukromé prostředky v součásti  
 Počítání odkazů probíhá na úrovni součásti. V důsledku toho, že kombinace sdílených a privátních prostředků v jedné součásti znemožňuje aktualizaci privátních prostředků, jako je spustitelný soubor, bez nutnosti přepsat sdílené prostředky. Tento scénář vytvoří problémy s nekompatibilitou a omezí vám vytváření souběžných funkcí.  
  
 Například hodnoty registru, které slouží k registraci VSPackage pomocí, [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)] by měly být uchovávány v komponentě oddělené od verze používané k registraci VSPackage pomocí [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] . Sdílené soubory nebo hodnoty registru jdou ještě jinou součástí.  
  
## <a name="scenario-1-shared-vspackage"></a>Scénář 1: sdílený VSPackage  
 V tomto scénáři je sdílený VSPackage (jeden binární soubor, který podporuje více verzí [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] ) dodán v balíčku Instalační služba systému Windows. Registrace s každou verzí nástroje [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] je řízena funkcemi, které si vyberete uživatelem. Také to znamená, že při přiřazení k samostatným funkcím je možné každou komponentu vybrat jednotlivě pro instalaci nebo odinstalaci, přičemž uživatel bude řídit integraci rozhraní VSPackage do různých verzí nástroje [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] . (Další informace o používání funkcí v balíčcích Instalační služba systému Windows najdete v tématu [funkce instalační služba systému Windows](https://msdn.microsoft.com/library/aa372840\(VS.85\).aspx) .)  
  
 ![Obrázek VS Shared VSPackage](../../extensibility/internals/media/vs-sharedpackage.gif "VS_SharedPackage")  
Shared VSPackage – instalační program  
  
 Jak je znázorněno na obrázku, sdílené součásti jsou součástí funkce Feat_Common, která je vždy nainstalována. Díky tomu, že se funkce Feat_VS2002 a Feat_VS2003 zobrazí, mohou uživatelé zvolit v době instalace, do které verze chtějí sadu [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] VSPackage integrovat. Uživatelé můžou k přidávání nebo odebírání funkcí použít taky režim údržby Instalační služba systému Windows, který v tomto případě přidává nebo odebírá registrační informace VSPackage z různých verzí nástroje [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] .  
  
> [!NOTE]
> Nastavení zobrazení sloupce funkce na hodnotu 0 skryje. Hodnota sloupce nízké úrovně, například 1, zajistí, že bude vždy nainstalována. Další informace najdete v tématu [vlastnost INSTALLLEVEL](https://msdn.microsoft.com/library/aa369536\(VS.85\).aspx) a [Tabulka funkcí](https://msdn.microsoft.com/library/aa368585.aspx).  
  
## <a name="scenario-2-shared-vspackage-update"></a>Scénář 2: sdílená aktualizace VSPackage  
 V tomto scénáři je dodávána aktualizovaná verze instalačního programu VSPackage ve scénáři 1. Pro účely diskuze aktualizace přidává podporu pro [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] , ale může to být také zjednodušená Oprava zabezpečení nebo aktualizace Service Pack s chybou. Pravidla Instalační služba systému Windows pro instalaci novějších komponent vyžadují, aby nezměněné součásti již v systému nebyly překopírovány. V takovém případě systém s verzí 1,0 již existuje, přepíše aktualizovanou součást Comp_MyVSPackage.dll a umožní uživatelům přidat novou funkci Feat_VS2005 pomocí Comp_VS2005_Reg komponenty.  
  
> [!CAUTION]
> Pokaždé, když se VSPackage sdílí mezi více verzemi nástroje [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] , je nezbytné, aby následující verze balíčku VSPackage udržovaly zpětnou kompatibilitu s předchozími verzemi nástroje [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] . Pokud nemůžete zachovat zpětnou kompatibilitu, je nutné použít souběžné soukromé VSPackage. Další informace najdete v tématu [Podpora více verzí sady Visual Studio](../../extensibility/supporting-multiple-versions-of-visual-studio.md).  
  
 ![Obrázek aktualizace balíčku vs Shared VS](../../extensibility/internals/media/vs-sharedpackageupdate.gif "VS_SharedPackageUpdate")  
Instalační program pro Shared VSPackage Update  
  
 Tento scénář prezentuje nový instalační program VSPackage s využitím podpory Instalační služba systému Windows pro menší upgrady. Uživatelé jednoduše nainstalují verzi 1,1 a upgradují verzi 1,0. Není však nutné mít v systému verzi 1,0. Stejný instalační program nainstaluje verzi 1,1 na systém bez verze 1,0. Výhodou pro zajištění menších upgradů je to, že nemusíte přecházet na práci s vývojem instalačního programu pro upgrade a úplného instalačního programu produktu. Jeden instalační program provede obě úlohy. Oprava zabezpečení nebo aktualizace Service Pack může místo toho využít výhod Instalační služba systému Windowsch oprav. Další informace najdete v tématu [opravy a upgrady](https://msdn.microsoft.com/library/aa370579\(VS.85\).aspx).  
  
## <a name="scenario-3-side-by-side-vspackage"></a>Scénář 3: souběžný VSPackage  
 Tento scénář prezentuje dva instalační programy VSPackage – jeden pro každou verzi sady Visual Studio .NET 2003 a [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] . Každý instalační program nainstaluje souběžnou nebo soukromou sadu VSPackage (ta, která je speciálně sestavená a nainstalovaná pro konkrétní verzi nástroje [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] ). Každý VSPackage je ve své vlastní součásti. V důsledku toho je každý z nich možné jednotlivě obsluhovat pomocí oprav nebo verzí údržby. Vzhledem k tomu, že knihovna VSPackage je nyní specifická pro verzi, je bezpečné zahrnout informace o registraci do stejné součásti jako knihovnu DLL.  
  
 ![&#45;na straně&#45;na straně obrázku VS. grafika balíčku](../../extensibility/internals/media/vs-sbys-package.gif "VS_SbyS_Package")  
Souběžná instalace balíčku VSPackage  
  
 Každý instalační program obsahuje také kód, který je sdílen mezi oběma instalačními programy. Pokud je sdílený kód nainstalován do společného umístění, instalace obou souborů. msi nainstaluje pouze jeden sdílený kód. Druhý instalační program pouze zvyšuje počet odkazů na součást. Počet odkazů zajišťuje, že pokud dojde k odinstalování jednoho ze VSPackage, sdílený kód zůstane pro druhý VSPackage. Pokud je druhý VSPackage odinstalován také, bude sdílený kód odebrán.  
  
## <a name="scenario-4-side-by-side-vspackage-update"></a>Scénář 4: souběžná aktualizace VSPackage na straně  
 V tomto scénáři jste si VSPackage [!INCLUDE[vsprvslong](../../includes/vsprvslong-md.md)] z důvodu ohrožení zabezpečení a potřebujete vydat aktualizaci. Stejně jako ve scénáři 2 můžete vytvořit nový soubor. msi, který aktualizuje existující instalaci, aby zahrnoval opravu zabezpečení, a taky nasadit nové instalace s opravou zabezpečení, které už jsou v platnosti.  
  
 V tomto případě je VSPackage spravovaným rozhraním VSPackage nainstalovaným v globální mezipaměti sestavení (GAC). Při opětovném sestavení, aby zahrnoval opravu zabezpečení, je nutné změnit číslo verze revize čísla verze sestavení. Informace o registraci pro nové číslo verze sestavení přepíší předchozí verzi, což by způsobilo [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] načtení pevného sestavení.  
  
 ![&#45;na straně a na&#45;straně VS – obrázek aktualizace balíčku VS](../../extensibility/internals/media/vs-sbys-packageupdate.gif "VS_SbyS_PackageUpdate")  
Instalační program pro souběžnou aktualizaci VSPackage  
  
 **Poznámka:** Další informace o nasazení souběžných sestavení naleznete v tématu [zjednodušení nasazení a řešení Hell DLL pomocí .NET Framework](https://msdn.microsoft.com/library/ms973843.aspx).  
  
## <a name="see-also"></a>Viz také  
 [Instalační služba systému Windows](https://msdn.microsoft.com/library/cc185688\(VS.85\).aspx)   
 [Podpora více verzí sady Visual Studio](../../extensibility/supporting-multiple-versions-of-visual-studio.md)
