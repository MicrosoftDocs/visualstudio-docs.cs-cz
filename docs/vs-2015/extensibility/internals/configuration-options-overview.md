---
title: Možnosti konfigurace – přehled | Dokumentace Microsoftu
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
- project configurations
- configuration options, about configuration options
ms.assetid: f4ad4dd3-b39e-42df-ad89-d403cdf24a2b
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 44c5f424ec36d3c04403f62547920f59622208a9
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51747993"
---
# <a name="configuration-options-overview"></a>Přehled možností konfigurace
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Projekty v [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] může podporovat více konfigurací, které je možné sestavit, ladění, běhu a/nebo nasazené. Konfigurace je popsané společně s pojmenovanou sadu vlastností, obvykle přepínače kompilátoru a umístění souborů typu sestavení. Ve výchozím nastavení nová řešení obsahovat dvě konfigurace Debug a Release. Tyto konfigurace lze použít pomocí jejich výchozí nastavení, nebo upravit tak, aby podle svých specifických požadavků řešení nebo projektu. Některé balíčky se dají dvěma způsoby: jako ActiveX editor nebo jako součást na místě. Projekty není nutné pro podporu více konfigurací, ale. Pokud není k dispozici pouze jedné konfigurace, tuto konfiguraci je namapována na všechny konfigurace řešení.  
  
 Konfigurace se obvykle skládají ze dvou částí – název konfigurace (například ladění a vydání) a nastavení platformy. Název platformy konfigurace identifikuje prostředí, které nastavení konfigurace cíle, jako je například rozhraní API nebo platformu operačního systému. Uživatelé [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] nelze vytvořit platformu; musí zvolit ze výběr projektu umožňuje VSPackage. Když uživatel nainstaluje VSPackage platformu doručování vytvořené při vývoji v balíčku můžete surface libovolný název platformy desired podle jakékoli kritéria stanovená Tvůrce balíčku. Uživatel může vyberte ze seznamu platformy, které jsou k dispozici prostřednictvím sady VSPackage, když jsou vytvořeny na stránkách vlastností.  
  
 Platforma názvy jsou volitelné, protože ne všechny projekty podporují koncept platformy. Při konfiguraci chybí název platformy, zobrazí se v uživatelském rozhraní řetězec "není k dispozici".  
  
 Každé řešení má svou vlastní sadu konfigurací, jenom jeden z nich může být současně aktivní. Konfigurace řešení je sada více než jednu konfiguraci z každého projektu. Uvedení "více než" je možnost vyloučit projektu z konfigurace řešení. Uživatelé můžou vytvářet své vlastní konfigurace vlastní řešení.  
  
 Následující tabulka ukazuje typické konfigurace nastavení pro projekt. Řádky jsou označeny jako s názvy konfigurací a sloupce s názvy platformy.  
  
|Název konfigurace|Platforma – Win32|Platforma – Win64|  
|------------------------|----------------------|----------------------|  
|Ladit|\<Win32 nastavení ladění >|\<Nastavení Win64 ladění >|  
|Vydaná verze|\<Verze Win32 Nastavení >|\<Nastavení Win64 vydání >|  
|MyConfig|Není k dispozici|\<Nastavení MyConfig Win64 >|  
  
> [!NOTE]
>  Nelze vytvořit konfigurace řešení "MyConfig", který vylučuje platformy "Win32", není-li projekt, který cílíte nepodporuje Win32.  
  
 Změna aktivní konfigurace řešení vybere sadu konfigurace projektu, které jsou vytvořené, spouštět, ladit nebo nasazení v tomto řešení. Například pokud změníte konfiguraci aktivního řešení od vydání verze pro ladění, všechny projekty v rámci tohoto řešení jsou automaticky vytvořené s konfigurací projektu uvedené v konfiguraci řešení ladění. Konfigurace projektu jsou obvykle také pojmenované ladění pouze tehdy, pokud uživatel má ručních změn v prostředí Configuration Manageru.  
  
 Součástí vlastností konfigurace řešení uložené u každého projektu i název projektu, název konfigurace projektu, příznaky označující, jestli se k sestavení nebo nasazení a název platformy. Další informace najdete v tématu [konfigurace řešení](../../extensibility/internals/solution-configuration.md).  
  
 Uživatel můžete zobrazit a nastavte parametry konfigurace řešení vyberte řešení v hierarchii (Průzkumníku řešení) a otevřením stránky vlastností. Podobně můžete zobrazit a nastavte parametry konfigurace projektu výběrem projektu v Průzkumníku řešení a otevřením stránky vlastností pro daný projekt.  
  
 Uživatele můžete také vytvořit jeden projekt pomocí konfigurační nastavení vydání a všechny ostatní konfigurace nastavení pro ladění v případě potřeby. Další informace najdete v tématu [konfigurace projektu pro sestavení](../../extensibility/internals/project-configuration-for-building.md).  
  
 Následující diagram znázorňuje, jak se implementují rozhraní, která podporují konfigurace řešení a projektu:  
  
 ![Obrázek konfigurace rozhraní](../../extensibility/internals/media/vsconfiginterfaces.gif "vsConfigInterfaces")  
Rozhraní pro konfiguraci  
  
 Několik poznámek týkajících se na předchozím obrázku:  
  
- `IDispatch` je označen jako volitelné v objektu konfigurace. Konkrétně je volitelný, aby rozhraní konfigurace v objektu Procházet.  
  
- `IVsDebuggableProjectCfg` je označen jako volitelný v objekt konfigurace, ale je vyžadováno pro podporu ladění.  
  
- `IVsProjectCfg2` je označen jako volitelný v objekt konfigurace, ale je potřeba pro podporu seskupování výstup.  
  
- `Config Provider` Objekt je označen jako objekt volitelné, ale možnost je tam, kde na jeho implementaci. Objekt může implementovat na objekt projektu nebo na samostatném objektu.  
  
- `IVsCfgProvider2` je potřeba pro podporu platforem a úpravu konfigurace. `IVsCfgProvider` Stačí, pokud není implementace, které tuto funkci.  
  
- Některé z těchto objektů je vidět na obrázku jako samostatné objekty je možné kombinovat do stejné třídy, kde je to praktické podle požadavků konkrétního návrhu. V dalších tématech v této části ale objekty a rozhraní přidružené k těmto objektům probereme podle scénáře uvedené v diagramu.  
  
- Některé objekty jsou implementovány samostatně. Projekt a sestavení řešení, například probíhat v samostatných vláknech a objekt, který chcete spravovat život sestavení odděleně od objektu popisující konfiguraci sestavení.  
  
  Další informace o rozhraní objekt konfigurace a objekt konfigurace poskytovatele rozhraní na předchozím obrázku, naleznete v tématu [objekt konfigurace projektu](../../extensibility/internals/project-configuration-object.md). Kromě toho [konfigurace projektu pro sestavení](../../extensibility/internals/project-configuration-for-building.md) poskytuje další informace o rozhraní Configuration Builder a objekt závislosti sestavení a [konfigurace projektu pro správu nasazení](../../extensibility/internals/project-configuration-for-managing-deployment.md) Dále popisuje rozhraní připojené ke konfiguraci nástroje pro nasazení a nasazení objekty závislosti. Nakonec [konfigurace projektu pro výstup](../../extensibility/internals/project-configuration-for-output.md) popisuje rozhraní výstupní skupinu a výstupní objekt a použijte stránky vlastností k zobrazení a nastavit vlastnosti závislé na konfiguraci.  
  
## <a name="see-also"></a>Viz také  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2>   
 [Konfigurace projektu pro sestavení](../../extensibility/internals/project-configuration-for-building.md)   
 [Konfigurace řešení](../../extensibility/internals/solution-configuration.md)

