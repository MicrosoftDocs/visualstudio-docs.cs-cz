---
title: Výběr a Měna v prostředí IDE | Dokumentace Microsoftu
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
- currency, Visual Studio IDE
- IDE, selection
- selection, Visual Studio IDE
- IDE, currency
ms.assetid: 2f6f18d1-acd8-454d-a856-9a4d81155052
caps.latest.revision: 15
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 45fc57bf2d5763527f9f8c2c6d8d22ca1d6369f8
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51786740"
---
# <a name="selection-and-currency-in-the-ide"></a>Výběr a měna v prostředí IDE
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Integrované vývojové prostředí (IDE) uchovává informace o uživatelích aktuálně vybrané objekty s použitím výběru *kontextu*. Výběr kontextu rozšíření VSPackages dá využít v místní měně sledování dvěma způsoby:  
  
-   Pomocí šíření měny informace o rozšíření VSPackages rozhraní IDE.  
  
-   Díky monitorování výběry aktuálně aktivních uživatelů v rámci rozhraní IDE.  
  
## <a name="selection-context"></a>Kontext výběru  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] IDE globálně uchovává informace o měně integrovaného vývojového prostředí ve své vlastní objekt kontextu globálního výběru. Následující tabulka uvádí prvky, které tvoří kontext výběru.  
  
|Prvek|Popis|  
|-------------|-----------------|  
|Aktuální hierarchií|Obvykle aktuálním projektu. aktuální hierarchií NULL znamená, že je aktuální řešení jako celek.|  
|ID aktuální položky|Vybranou položku v rámci aktuální hierarchii. Pokud existuje více výběrů, v okně projektu, může být více aktuální položky.|  
|aktuální `SelectionContainer`|Obsahuje jeden nebo více objektů, u kterých by měl zobrazit v okně Vlastnosti vlastnosti.|  
  
 Kromě toho prostředí udržuje dvě globální seznamy:  
  
-   Seznam identifikátorů aktivní příkaz uživatelského rozhraní  
  
-   Seznam typů aktuálně aktivním prvkem.  
  
### <a name="window-types-and-selection"></a>Typy oken a výběr  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Integrovaném vývojovém prostředí slouží k uspořádání windows na dvě obecné typy:  
  
- Typ hierarchie windows  
  
- Oken s rámečkem, jako je například oken nástrojů a dokumentu  
  
  Rozhraní IDE sleduje měny odlišně pro každý z těchto typů okna.  
  
  Okno nejběžnější typ projektu je Průzkumníku řešení, které řídí integrovaného vývojového prostředí. Okno typu projektu sleduje globální hierarchie a ItemID globální výběr kontextu a v okně spoléhá na výběru uživatele k určení aktuální hierarchií. Pro typ projektu windows prostředí poskytuje globální službu <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection>, pomocí které rozšíření VSPackages můžete monitorovat aktuální hodnoty pro otevřené elementy. V prostředí pro procházení vlastností doprovází této globální služby.  
  
  Oken s rámečkem na druhé straně vytisknout tak, aby nabízel SelectionContext hodnoty (hierarchie/ItemID/SelectionContainer trojici komponent) použít v rámci okna rámce. . Použití oken s rámečkem služby <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> pro tento účel. Vytisknout lze vkládat pouze hodnoty pro zásobník pro výběr, byste museli opustit místní hodnoty pro hierarchii a ItemID beze změny, jako je typický pro dokumenty podřízeného MDI.  
  
### <a name="events-and-currency"></a>Události a měny  
 Může dojít k dva typy událostí, které mají vliv prostředí pojem měny:  
  
-   Události, které se rozšíří na globální úrovni a změňte výběr kontextu okna rámce. Tento druh událostí příklady podřízené okno MDI otevře, otevíraný panel globální nástrojů nebo panelu nástrojů typ projektu se otevře.  
  
-   Události, které prvky trasovány v rámci okna rámce výběru změnit. Mezi příklady patří změna výběru v rámci DocObject nebo změna výběru v okně Typ projektu.  
  
## <a name="see-also"></a>Viz také  
 [Kontextové objekty výběru](../../extensibility/internals/selection-context-objects.md)   
 [Zpětná vazba pro uživatele](../../extensibility/internals/feedback-to-the-user.md)

