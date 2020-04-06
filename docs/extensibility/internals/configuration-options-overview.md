---
title: Přehled možností konfigurace | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project configurations
- configuration options, about configuration options
ms.assetid: f4ad4dd3-b39e-42df-ad89-d403cdf24a2b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6d5ac25fcef7b942b791402baf17982c9810e92a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709413"
---
# <a name="configuration-options-overview"></a>Přehled možností konfigurace
Projekty [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] v programu podporují více konfigurací, které lze sestavit, ladit, spustit nebo nasadit. Konfigurace je typ sestavení popsaný s pojmenovanou sadou vlastností, obvykle přepínačů kompilátoru a umístění souborů. Ve výchozím nastavení nová řešení obsahují dvě konfigurace, *Ladění* a *Vydání*. Tyto konfigurace lze použít pomocí výchozího nastavení nebo upravit tak, aby splňovaly vaše konkrétní požadavky na řešení nebo projekt. Některé balíčky lze sestavit dvěma způsoby: jako editor ActiveX nebo jako součást na místě. Projekty však nemusí podporovat více konfigurací. Pokud je k dispozici pouze jedna konfigurace, je tato konfigurace mapována do všech konfigurací řešení.

 Konfigurace se obvykle skládají ze dvou částí: název konfigurace (například *Ladění* nebo *vydání)* a nastavení platformy. Název platformy konfigurace identifikuje prostředí, na které se konfigurace zaměřuje, například na sadu rozhraní API nebo platformu operačního systému. Uživatelé [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] aplikace nemůže vytvořit platformu; musí vybrat z výběrů projektu VSPackage umožňuje. Když uživatel nainstaluje VSPackage, doručovací platforma vytvořená během vývoje balíčku může vyskakovat libovolný název platformy požadovaný na základě všech kritérií nastavených tvůrcem balíčku. Uživatel pak můžete vybrat ze seznamu platforem k dispozici prostřednictvím VSPackage při vytváření instancí vlastností.

 Názvy platforem jsou volitelné, protože ne všechny projekty podporují koncepci platforem. Pokud konfigurace postrádá název platformy, řetězec **Není k tomu do)v** uživatelském uživatelském nastavení.

 Každé řešení má vlastní sadu konfigurací, z nichž pouze jedna může být aktivní najednou. Konfigurace řešení je sada ne více než jednu konfiguraci z každého projektu. "Ne více než" podmínka je kvůli možnosti vyloučit projekt z konfigurace řešení. Uživatelé mohou vytvářet vlastní konfigurace řešení.

 Následující tabulka znázorňuje typické konfigurace nastavení projektu. Řádky jsou označeny názvy konfigurace a sloupci s názvy platformy.

|Název konfigurace|Platforma: Win32|Platforma: Win64|
|------------------------|----------------------|----------------------|
|*Ladit*|\<Ladění nastavení win32>|\<Ladění nastavení Win64>|
|*Vydat*|\<Uvolnění> nastavení win32|\<Vydání> nastavení win64|
|*MyConfig*|Není dostupné.|\<MyConfig Win64 nastavení>|

> [!NOTE]
> Nelze vytvořit konfiguraci řešení *MyConfig,* která vylučuje platformu Win32, pokud projekt, na který cílíte, nepodporuje win32.

 Změna aktivní konfigurace řešení vybere sadu konfigurací projektu, která je sestavena, spuštěna, laděna nebo nasazena v tomto řešení. Pokud například změníte konfiguraci aktivního řešení z *verze* na *ladění*, všechny projekty v rámci tohoto řešení jsou automaticky vytvořeny s konfigurací projektů uvedenou v konfiguraci ladění řešení. Konfigurace projektů jsou také pojmenovány *Ladění,* pokud uživatel provedl ruční změny v konfiguračním správci prostředí.

 Vlastnosti konfigurace řešení uložené pro každý projekt zahrnují název projektu, název konfigurace projektu, příznaky označující, zda chcete sestavit nebo nasadit, a název platformy. Další informace naleznete v [tématu Konfigurace řešení](../../extensibility/internals/solution-configuration.md).

 Uživatel může zobrazit a nastavit parametry konfigurace řešení výběrem řešení v hierarchii (Průzkumník řešení) a otevřením stránek vlastností. Podobně můžete zobrazit a nastavit parametry konfigurace projektu výběrem projektu v Průzkumníku řešení a otevřením stránek vlastností pro tento projekt.

 Uživatel může také vytvořit jeden projekt pomocí nastavení konfigurace verze a všechny ostatní s nastavením konfigurace ladění v případě potřeby. Další informace naleznete v [tématu Konfigurace projektu pro vytváření](../../extensibility/internals/project-configuration-for-building.md).

 Následující diagram znázorňuje, jak jsou implementována rozhraní, která podporují řešení a konfigurace projektu:

 ![Obrázek konfiguračních rozhraní](../../extensibility/internals/media/vsconfiginterfaces.gif "vsConfigInterfaces") Konfigurační rozhraní

 Několik poznámek týkajících se předchozího diagramu:

- `IDispatch`je v konfiguračním objektu označen jako volitelný. Konkrétně je volitelné mít konfigurační rozhraní na procházet objektu.

- `IVsDebuggableProjectCfg`je v objektu konfigurace označen jako volitelný, ale je vyžadován pro podporu ladění.

- `IVsProjectCfg2`je v objektu konfigurace označen jako volitelný, ale je potřebný pro podporu seskupení výstupu.

- Objekt Config Provider je označen jako volitelný objekt, ale možnost je, kde jej implementovat. Objekt můžete implementovat na objekt u projektu nebo na samostatný objekt.

- `IVsCfgProvider2`je potřeba pro podporu platformy a úpravy konfigurace. `IVsCfgProvider`je dostačující, pokud tuto funkci neimplementujete.

- Některé z těchto objektů uvedených v diagramu jako samostatné objekty mohou být sloučeny do stejné třídy, kde je to praktické na základě vašich specifických požadavků na návrh. V jiných tématech této části však objekty a rozhraní přidružené k těmto objektům budou popsány podle scénáře uvedeného v diagramu.

- Některé objekty jsou implementovány samostatně. Například projekt a řešení sestavení dojít na samostatné podprocesy a objekt pro správu sestavení žije odděleně od objektu popisující konfigurace pro sestavení.

  Další informace o rozhraních konfiguračních objektů a rozhraních objektů zprostředkovatele konfigurace v předchozím diagramu naleznete v [tématu Project configuration object](../../extensibility/internals/project-configuration-object.md). Kromě toho [konfigurace aplikace Project pro vytváření](../../extensibility/internals/project-configuration-for-building.md) poskytuje další informace o rozhraní chodtvůrce konfigurace a sestavení závislost objektu a konfigurace aplikace pro [správu nasazení](../../extensibility/internals/project-configuration-for-managing-deployment.md) dále popisuje rozhraní připojená k nasazení konfigurace a objekty závislostí nasazení. Nakonec [konfigurace aplikace Project pro výstup](../../extensibility/internals/project-configuration-for-output.md) popisuje výstupní skupinu a rozhraní výstupního objektu a použití stránek vlastností k zobrazení a nastavení vlastností závislých na konfiguraci.

## <a name="see-also"></a>Viz také
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2>
- [Konfigurace projektu pro vytváření](../../extensibility/internals/project-configuration-for-building.md)
- [Konfigurace řešení](../../extensibility/internals/solution-configuration.md)
