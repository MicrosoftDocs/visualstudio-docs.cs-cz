---
title: Přehled možností konfigurace | Microsoft Docs
description: Seznamte se s možnostmi konfigurace projektu v aplikaci Visual Studio. Konfigurace je typ sestavení popsaný s pojmenovanou sadou vlastností a umístění souborů.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project configurations
- configuration options, about configuration options
ms.assetid: f4ad4dd3-b39e-42df-ad89-d403cdf24a2b
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: aa018d340e016ba5c9f424f705599a150ecdc818
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99884686"
---
# <a name="configuration-options-overview"></a>Přehled možností konfigurace
Projekty v [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] můžou podporovat více konfigurací, které se dají sestavit, ladit, spouštět nebo nasazovat. Konfigurace je typ sestavení popsaný s pojmenovanou sadou vlastností, obvykle se jedná o přepínače kompilátoru a umístění souborů. Ve výchozím nastavení obsahují nová řešení dvě konfigurace, *ladění* a *vydání*. Tyto konfigurace je možné použít s jejich výchozími nastaveními nebo úpravou tak, aby splňovaly vaše specifické požadavky řešení nebo projektu. Některé balíčky lze sestavit dvěma způsoby: jako editor ActiveX nebo jako místní komponenta. Projekty však nepotřebují podporovat více konfigurací. Pokud je k dispozici pouze jedna konfigurace, je tato konfigurace namapována na všechny konfigurace řešení.

 Konfigurace se typicky skládají ze dvou částí: název konfigurace (například *ladění* nebo *vydání*) a nastavení platformy. Název platformy konfigurace identifikuje prostředí, které cílí na konfiguraci, jako je sada rozhraní API nebo platforma operačního systému. Uživatelé [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] nemůžou vytvořit platformu. musí si vybrat z výběrů, které umožňuje projekt VSPackage. Když uživatel nainstaluje VSPackage, platforma pro doručování vytvořená během vývoje balíčku může vytvořit plochu podle požadovaného názvu platformy na základě libovolných kritérií nastavených tvůrcem balíčku. Uživatel pak může vybrat ze seznamu platforem, které jsou k dispozici prostřednictvím rozhraní VSPackage při vytváření instance stránek vlastností.

 Názvy platforem jsou nepovinné, protože ne všechny projekty podporují koncept platforem. Pokud v konfiguraci chybí název platformy, řetězec **N/a** se zobrazí v uživatelském rozhraní.

 Každé řešení má svou vlastní sadu konfigurací, v jednom okamžiku může být aktivní pouze jeden z nich. Konfigurace řešení je sada o více než jedné konfiguraci z každého projektu. Termín "ne více než" vychází z možnosti vyloučení projektu z konfigurace řešení. Uživatelé můžou vytvářet vlastní vlastní konfigurace řešení.

 Následující tabulka ilustruje typické nastavení konfigurace pro projekt. Řádky jsou označeny názvy konfigurace a sloupci s názvy platforem.

|Název konfigurace|Platforma: Win32|Platforma: Win64|
|------------------------|----------------------|----------------------|
|*Ladění*|\<Debug Win32 settings>|\<Debug Win64 settings>|
|*Vydaná verze*|\<Release Win32 settings>|\<Release Win64 settings>|
|*MyConfig*|–|\<MyConfig Win64 settings>|

> [!NOTE]
> Nemůžete vytvořit konfiguraci řešení *MyConfig* , která vylučuje platformu Win32, pokud projekt, který necílíte, nepodporuje Win32.

 Změna aktivní konfigurace pro řešení vybere sadu konfigurací projektu, které jsou sestaveny, spouštěny, laděny nebo nasazeny v tomto řešení. Například pokud změníte aktivní konfiguraci řešení z vydaných *verzí* na *ladit*, všechny projekty v tomto řešení budou automaticky vytvořeny s konfigurací projektů, které jsou uvedeny v konfiguraci ladění řešení. Konfigurace projektů se také nazývají *ladit* , pokud uživatel neudělal v Configuration Manager prostředí ruční změny.

 Vlastnosti konfigurace řešení uložené pro každý projekt obsahují název projektu, název konfigurace projektu, příznaky k označení, zda má být sestavení nebo nasazení a název platformy. Další informace najdete v tématu věnovaném [konfiguraci řešení](../../extensibility/internals/solution-configuration.md).

 Uživatel může zobrazit a nastavit parametry konfigurace řešení tak, že vybere řešení v hierarchii (Průzkumník řešení) a otevírá stránky vlastností. Podobně můžete zobrazit a nastavit parametry konfigurace projektu výběrem projektu v Průzkumník řešení a otevřením stránky vlastností pro daný projekt.

 Uživatel může také vytvořit jeden projekt pomocí nastavení konfigurace vydání a všech zbývajících s nastavením konfigurace ladění v případě potřeby. Další informace najdete v tématu [konfigurace projektu pro sestavování](../../extensibility/internals/project-configuration-for-building.md).

 Následující diagram znázorňuje, jak jsou implementovány rozhraní podporující konfigurace řešení a projektu:

 ![Rozhraní pro konfiguraci – grafika](../../extensibility/internals/media/vsconfiginterfaces.gif "vsConfigInterfaces") Konfigurační rozhraní

 Pár poznámek vztahujících se k předchozímu diagramu:

- `IDispatch` je v objektu konfigurace označen jako volitelné. Konkrétně je volitelné mít konfigurační rozhraní objektu procházení.

- `IVsDebuggableProjectCfg` je v objektu konfigurace označen jako volitelné, ale vyžaduje se pro podporu ladění.

- `IVsProjectCfg2` je označen jako volitelné v objektu konfigurace, ale je potřeba pro podporu seskupení výstupu.

- Objekt zprostředkovatele konfigurace je označen jako volitelný objekt, ale možnost je místo toho implementovat. Můžete implementovat objekt na objekt projektu nebo na samostatném objektu.

- `IVsCfgProvider2` je potřeba pro podporu platforem a úpravy konfigurace. `IVsCfgProvider` je dostačující, pokud neimplementujete tuto funkci.

- Některé z těchto objektů zobrazených v diagramu jako samostatné objekty mohou být kombinovány do stejné třídy, kde to bude praktické na základě konkrétních požadavků na návrh. V jiných tématech této části se ale objekty a rozhraní přidružené k těmto objektům projednávají v závislosti na scénáři uvedeném v diagramu.

- Určité objekty jsou implementovány samostatně. Například při sestavování projektů a řešení dochází v samostatných vláknech a objekt pro správu sestavení v nezávisle na objektu, který popisuje konfiguraci pro sestavení.

  Další informace o rozhraních konfiguračního objektu a rozhraních objektů poskytovatele konfigurace v předchozím diagramu naleznete v tématu [objekt konfigurace projektu](../../extensibility/internals/project-configuration-object.md). Kromě toho [konfigurace projektu pro sestavování](../../extensibility/internals/project-configuration-for-building.md) poskytuje další informace o rozhraních nástroje Configuration Builder a o rozhraních objektů závislosti sestavení a [konfigurace projektu pro správu nasazení](../../extensibility/internals/project-configuration-for-managing-deployment.md) dále popisuje rozhraní připojená k nástrojům pro nasazení konfigurace a objektům závislosti nasazení. Nakonec [konfigurace projektu pro výstup](../../extensibility/internals/project-configuration-for-output.md) popisuje výstupní skupinu a výstupní rozhraní objektů a použití stránek vlastností k zobrazení a nastavení vlastností závislých na konfiguraci.

## <a name="see-also"></a>Viz také
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2>
- [Konfigurace projektu pro sestavení](../../extensibility/internals/project-configuration-for-building.md)
- [Konfigurace řešení](../../extensibility/internals/solution-configuration.md)
