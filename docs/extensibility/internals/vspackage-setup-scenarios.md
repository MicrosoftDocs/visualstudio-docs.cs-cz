---
title: Scénáře instalace VSPackage | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, deployment considerations
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 01279666642adb729d4350b8a497c42d78159120
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "80703976"
---
# <a name="vspackage-setup-scenarios"></a>Scénáře instalace balíčku VSPackage

Je důležité navrhnout instalační program VSPackage pro flexibilitu. Například může být potřeba opravit opravu zabezpečení v budoucnu nebo můžete změnit obchodní strategii, která vyžaduje důkladnou podporu souběžného používání verzí.

V [podpoře více verzí sady Visual Studio](../../extensibility/supporting-multiple-versions-of-visual-studio.md)si můžete přečíst informace o výhodách a potížích s podporou souběžných instalací [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] s buď sdílených nebo souběžnými instalacemi sady VSPackage. V krátkých a souběžných rozhraních VSPackage získáte největší flexibilitu při podpoře nových funkcí nástroje [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .

Scénáře popsané v tomto tématu nejsou vaší jedinou možností, ale zobrazují se jako doporučené osvědčené postupy.

## <a name="components-privacy-and-sharing"></a>Komponenty, ochrana osobních údajů a sdílení

### <a name="make-your-components-independent"></a>Nezávislé na komponentách

Jakmile identifikujete a naplníte komponentu, přiřadíte a `GUID` nasadíte komponentu, nemůžete změnit její složení. Pokud změníte kompozici komponenty, výsledná součást musí být novou součástí s novým `GUID` . Vzhledem k těmto skutečnostem je flexibilita nejvyšší verze zajištěna tím, že se každá komponenta nezávislá, samostatná jednotka. Další informace o pravidlech, kterými se řídí komponenty, naleznete v tématu [Změna kódu komponenty](/windows/desktop/Msi/changing-the-component-code) a [co se stane, pokud jsou pravidla komponent poškozena?](/windows/desktop/Msi/what-happens-if-the-component-rules-are-broken).

### <a name="do-not-mix-shared-and-private-resources-in-a-component"></a>Nemíchat sdílené a soukromé prostředky v součásti

Počítání odkazů probíhá na úrovni součásti. V důsledku toho, že kombinace sdílených a privátních prostředků v jedné součásti znemožňuje aktualizaci privátních prostředků, jako je spustitelný soubor, bez nutnosti přepsat sdílené prostředky. Tento scénář vytvoří problémy s nekompatibilitou a omezí vám vytváření souběžných funkcí.

Například hodnoty registru, které slouží k registraci VSPackage pomocí, [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] by měly být uchovávány v komponentě oddělené od verze, která se používá k registraci VSPackage v aplikaci Visual Studio. Sdílené soubory nebo hodnoty registru jdou ještě jinou součástí.

## <a name="scenario-1-shared-vspackage"></a>Scénář 1: sdílený VSPackage

V tomto scénáři je sdílený VSPackage (jeden binární soubor, který podporuje více verzí sady Visual Studio, dodán v balíčku Instalační služba systému Windows. Registrace v každé verzi sady Visual Studio je řízena funkcemi, které si vyberete uživatelem. Také to znamená, že při přiřazení k samostatným funkcím je možné každou komponentu vybrat jednotlivě pro instalaci nebo odinstalaci, přičemž uživatel bude řídit integraci rozhraní VSPackage do různých verzí nástroje [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . (Další informace o používání funkcí v balíčcích Instalační služba systému Windows najdete v tématu [funkce instalační služba systému Windows](/windows/desktop/Msi/windows-installer-features) .)

![Instalační program sady VSPackage VS Shared](../../extensibility/internals/media/vs_sharedpackage.gif "VS_SharedPackage")

Jak je znázorněno na obrázku, sdílené součásti jsou součástí funkce Feat_Common, která je vždy nainstalována. Díky tomu, že jsou viditelné funkce Feat_VS2002 a Feat_VS2003, mohou uživatelé zvolit v době instalace, do které verze sady Visual Studio chtějí sadu VSPackage integrovat. Uživatelé mohou také použít režim údržby Instalační služba systému Windows k přidání nebo odebrání funkcí, které v tomto případě přidávají nebo odstraňují registrační informace VSPackage z různých verzí sady Visual Studio.

> [!NOTE]
> Nastavení zobrazení sloupce funkce na hodnotu 0 skryje. Hodnota sloupce nízké úrovně, například 1, zajistí, že bude vždy nainstalována. Další informace najdete v tématu [vlastnost INSTALLLEVEL](/windows/desktop/Msi/installlevel) a [Tabulka funkcí](/windows/desktop/Msi/feature-table).

## <a name="scenario-2-shared-vspackage-update"></a>Scénář 2: sdílená aktualizace VSPackage

V tomto scénáři je dodávána aktualizovaná verze instalačního programu VSPackage ve scénáři 1. Pro účely diskuze aktualizace přidává podporu pro Visual Studio, ale může to být také zjednodušená Oprava zabezpečení nebo aktualizace Service Pack s chybou. Pravidla Instalační služba systému Windows pro instalaci novějších komponent vyžadují, aby nezměněné součásti již v systému nebyly překopírovány. V takovém případě systém s verzí 1,0 již existuje, přepíše aktualizovanou součást Comp_MyVSPackage.dll a umožní uživatelům přidat novou funkci Feat_VS2005 pomocí Comp_VS2005_Reg komponenty.

> [!CAUTION]
> Pokaždé, když se VSPackage sdílí mezi více verzemi nástroje [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] , je nezbytné, aby následující verze balíčku VSPackage udržovaly zpětnou kompatibilitu s předchozími verzemi sady Visual Studio. Pokud nemůžete zachovat zpětnou kompatibilitu, je nutné použít souběžné soukromé VSPackage. Další informace najdete v tématu [Podpora více verzí sady Visual Studio](../../extensibility/supporting-multiple-versions-of-visual-studio.md).

![Instalační program sady vs Shared VS Package Update](../../extensibility/internals/media/vs_sharedpackageupdate.gif "VS_SharedPackageUpdate")

Tento scénář prezentuje nový instalační program VSPackage s využitím podpory Instalační služba systému Windows pro menší upgrady. Uživatelé jednoduše nainstalují verzi 1,1 a upgradují verzi 1,0. Není však nutné mít v systému verzi 1,0. Stejný instalační program nainstaluje verzi 1,1 na systém bez verze 1,0. Výhodou pro zajištění menších upgradů je to, že nemusíte přecházet na práci s vývojem instalačního programu pro upgrade a úplného instalačního programu produktu. Jeden instalační program provede obě úlohy. Oprava zabezpečení nebo aktualizace Service Pack může místo toho využít výhod Instalační služba systému Windowsch oprav. Další informace najdete v tématu [opravy a upgrady](/windows/desktop/Msi/patching-and-upgrades).

## <a name="scenario-3-side-by-side-vspackage"></a>Scénář 3: souběžný VSPackage

Tento scénář představuje dva instalační programy VSPackage – jeden pro každou verzi sady Visual Studio .NET 2003 a Visual Studio. Každý instalační program nainstaluje souběžnou nebo soukromou sadu VSPackage (ta, která je speciálně sestavená a nainstalovaná pro konkrétní verzi sady Visual Studio). Každý VSPackage je ve své vlastní součásti. V důsledku toho je každý z nich možné jednotlivě obsluhovat pomocí oprav nebo verzí údržby. Vzhledem k tomu, že knihovna VSPackage je nyní specifická pro verzi, je bezpečné zahrnout informace o registraci do stejné součásti jako knihovnu DLL.

![A souběžně s instalačním balíčkem VS.](../../extensibility/internals/media/vs_sbys_package.gif "VS_SbyS_Package")

Každý instalační program obsahuje také kód, který je sdílen mezi oběma instalačními programy. Pokud je sdílený kód nainstalován do společného umístění, instalace obou souborů. msi nainstaluje pouze jeden sdílený kód. Druhý instalační program pouze zvyšuje počet odkazů na součást. Počet odkazů zajišťuje, že pokud dojde k odinstalování jednoho ze VSPackage, sdílený kód zůstane pro druhý VSPackage. Pokud je druhý VSPackage odinstalován také, bude sdílený kód odebrán.

## <a name="scenario-4-side-by-side-vspackage-update"></a>Scénář 4: souběžná aktualizace VSPackage na straně

V tomto scénáři se vašemu balíčku VSPackage pro Visual Studio neutrpěla chyba zabezpečení a Vy musíte vydat aktualizaci. Stejně jako ve scénáři 2 můžete vytvořit nový soubor. msi, který aktualizuje existující instalaci, aby zahrnoval opravu zabezpečení, a taky nasadit nové instalace s opravou zabezpečení, které už jsou v platnosti.

V tomto případě je VSPackage spravovaným rozhraním VSPackage nainstalovaným v globální mezipaměti sestavení (GAC). Při opětovném sestavení, aby zahrnoval opravu zabezpečení, je nutné změnit číslo verze revize čísla verze sestavení. Informace o registraci pro nové číslo verze sestavení přepíší předchozí verzi, což by způsobilo [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] načtení pevného sestavení.

![A souběžný instalační program aktualizace balíčku VS.](../../extensibility/internals/media/vs_sbys_packageupdate.gif "VS_SbyS_PackageUpdate")

Další informace o nasazení souběžných sestavení naleznete v tématu [zjednodušení nasazení a řešení Hell DLL pomocí .NET Framework](https://msdn.microsoft.com/library/ms973843.aspx).

## <a name="see-also"></a>Viz také

- [Instalační služba systému Windows](/windows/desktop/Msi/windows-installer-portal)
- [Podpora více verzí sady Visual Studio](../../extensibility/supporting-multiple-versions-of-visual-studio.md)
