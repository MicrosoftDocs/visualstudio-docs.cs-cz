---
title: Aspekty řešení v izolovaném prostoru | Dokumentace společnosti Microsoft
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.Project.SandboxedSolutions
- VS.SharePointTools.Security.SandboxedSolutions
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, sandboxed solutions
- sandboxed solutions [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, farm solutions
- farm solutions [SharePoint development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 2f9a5d0c439d619864cc6e9559608e3c3891fc7e
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49890033"
---
# <a name="sandboxed-solution-considerations"></a>Aspekty řešení v izolovaném prostoru
  *Řešení v izolovaném prostoru* jsou funkce v aplikaci Microsoft SharePoint 2010, která umožňuje lokality kolekce uživatelům odesílat své vlastní řešení vlastního kódu. Běžné řešení v izolovaném prostoru se uživatelé nahrání vlastní webové části.  
  
 Aplikace v izolovaném prostoru SharePoint běží v zabezpečeném, monitorovaném procesu, který má přístup k omezené součástí webové farmy. Microsoft SharePoint 2010 používá kombinaci funkcí, galerie řešení, řešení monitorování a ověření rozhraní umožňující řešení v izolovaném prostoru.  
  
## <a name="specify-project-trust-level"></a>Zadejte úroveň důvěryhodnosti projektu
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] podporuje řešení v izolovaném prostoru pomocí vlastnosti Boolean projektu volá *řešení v izolovaném prostoru*. Tuto vlastnost lze nastavit v každém okamžiku v projektu, nebo můžete zadat, když vytvoříte projekt v **Průvodce přizpůsobením SharePoint**.  
  
> [!NOTE]  
>  Změna *řešení v izolovaném prostoru* vlastnosti projektu po jeho vytvoření může dojít k chybám ověření.  
  
 Řešení se považuje za rozsahem farmy řešení, pokud *řešení v izolovaném prostoru* je nastavena na **false** nebo vyberete **nasadit jako řešení farmy** možnost. Ale toto řešení je zpracovávat odděleně od řešení farmy Pokud *řešení v izolovaném prostoru* je nastavena na **true** nebo vyberete **nasadit jako řešení v izolovaném prostoru** možnost v průvodci.  
  
## <a name="sharepoint-site-hierarchy"></a>Hierarchie webu služby SharePoint
 Chcete-li pochopit, jak v izolovaném prostoru řešení práce, pomáhá zjistit, že jsou Sharepointové weby hierarchické v oboru. K prvku na vrcholu se označuje jako webové farmy a další prvky jsou podřízené k ní:  
  
 Webová farma  
  
 Webová aplikace A  
  
 Server kolekce A1  
  
 A1a lokality  
  
 Webová aplikace B  
  
 Kolekce B1 lokality  
  
 B1a lokality  
  
 B1b lokality  
  
 Kolekce B2 lokality  
  
 B2a lokality  
  
 Jak je vidět, webové serverové farmy může obsahovat jeden nebo více webových aplikací, které pak může obsahovat jeden nebo více kolekcí webů, které mají podřízené lokality a tak dále. Změny provedené v jedné lokalitě kolekce vlivu pouze, který kolekce webů a žádné jiné. Změny provedené na úrovni webové farmy však vliv na všechny kolekce webů v serverové farmě.  
  
 Windows SharePoint Services (WSS) 3.0 umožňuje nasadit řešení pouze na úrovni farmy, ale [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] umožňuje nasazení na úrovni farmy (pro řešení farmy) nebo na úrovni kolekce webů (řešení v izolovaném prostoru).  
  
## <a name="why-sandboxed-solutions"></a>Proč řešení v izolovaném prostoru?
 WSS 3.0 řešení může být nasazeny pouze na úrovni farmy. To znamená, že potenciálně škodlivého nebo destabilizující řešení může být nasazený, která měla vliv na celý webové farmy a všechny další kolekce webů a aplikací, které běží pod ním. Pomocí řešení v izolovaném prostoru, ale můžete nasadit řešení na podoblasti farmy určité kolekci webů. K zajištění další ochrany, toto řešení se nenačetlo sestavení do hlavní [!INCLUDE[TLA2#tla_iis5](../sharepoint/includes/tla2sharptla-iis5-md.md)] procesu (*w3wp.exe*). Místo toho je načtena jako samostatný proces (*SPUCWorkerProcess.exe*). Tento proces se monitoruje a implementuje kvóty a omezení pro ochranu farmy z řešení v izolovaném prostoru, které provádějí škodlivé aktivity, například spuštěním úzkou smyček, které spotřebovávají cykly procesoru.  
  
## <a name="site-collection-solution-gallery"></a>Galerie řešení kolekce webů
 [!INCLUDE[sharepointShort](../sharepoint/includes/sharepointshort-md.md)] 2010 obsahuje funkce, která se označuje jako "galerii kolekce webů řešení." Tuto funkci můžete přistupovat ze stránky Centrální správy služby SharePoint 2010 nebo tak, že otevřete **Akce webu** nabídky, zvolíte **nastavení webu**a potom kliknete **řešení** odkaz pod **Galerie** na Sharepointovém webu. Galerie řešení se úložiště řešení, která umožňují správci kolekce webů pro správu řešení v jejich kolekcím webů.  
  
 Galerie řešení je do knihovny dokumentů, které jsou uložené v kořenovém adresáři webové stránky SharePoint. Galerie řešení nahradí šablony webu a podporuje balíčků řešení. Když balíčku řešení služby SharePoint (*.wsp*) nahraje soubor, se zpracovávají jako řešení v izolovaném prostoru.  
  
## <a name="sandboxed-solution-limitations"></a>Omezení řešení v izolovaném prostoru
 Po nasazení řešení v izolovaném prostoru, je omezený na pomoct snížit jakékoli ohrožení zabezpečení, které je možné, že pole funkce služby SharePoint, které jsou k dispozici. Některé z těchto omezení patří:  
  
- Řešení v izolovaném prostoru máte omezená podmnožina nasaditelné řešení prvky jsou pro ně dostupné. Potenciálně ohrožená šablon projektu služby SharePoint, jako jsou definice webů a pracovních postupů, nejsou k dispozici.  
  
- SharePoint běží v procesu kódu řešení v izolovaném prostoru (*SPUCWorkerProcess.exe*) oddělená od hlavní [!INCLUDE[TLA2#tla_iis5](../sharepoint/includes/tla2sharptla-iis5-md.md)] fond aplikací (*w3wp.exe*) procesu.  
  
- Mapované složky nelze přidat do projektu.  
  
- Typy, které do [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] sestavení Microsoft.Office.Server nelze použít v řešení v izolovaném prostoru. Navíc pouze typy, které do [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] sestavení Microsoft.SharePoint lze použít v řešení v izolovaném prostoru.  
  
  Je důležité si uvědomit, zadání řešení služby SharePoint jako řešení v izolovaném prostoru nemá žádný vliv na server SharePoint. pouze určuje, jak nasazení projektu služby SharePoint k Sharepointu z [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] a jaké sestavení, který se váže k. Neovlivňuje generované *.wsp* souboru a *.wsp* soubor neobsahuje žádná data, které přímo souvisí s *řešení v izolovaném prostoru* vlastnost.  
  
## <a name="capabilities-and-elements-in-sandboxed-solutions"></a>Funkce a prvky v řešení v izolovaném prostoru
 Řešení v izolovaném prostoru se podporují následující funkce a prvky:  
  
- Typy a pole obsahu  
  
- Vlastní akce  
  
- Deklarativní pracovních postupů  
  
- Přijímače událostí  
  
- Funkce popisky  
  
- Seznam definic  
  
- Instance seznamu  
  
- Soubory/modulu  
  
- Navigace  
  
- *Onet.XML*  
  
- SPItemEventReceiver  
  
- SPListEventReceiver  
  
- SPWebEventReceiver  
  
- Podpora pro všechny webové části, které jsou odvozeny z `System.Web.UI.WebControls.WebParts.WebPart`  
  
- Webové části  
  
- Elementy funkce WebTemplate (místo *Webtemp.xml*)  
  
- Vizuální webové části  
  
  Řešení v izolovaném prostoru nepodporuje následující funkce a prvky:  
  
- Stránky aplikací  
  
- Vlastní skupiny akcí  
  
- Funkce s oborem farmy  
  
- `HideCustomAction` – element  
  
- Web s rozsahem aplikace funkcí  
  
- Pracovní postupy s kódem  
  
## <a name="see-also"></a>Viz také:
 [Rozdíly mezi řešeními v izolovaném prostoru a ve farmách](../sharepoint/differences-between-sandboxed-and-farm-solutions.md)   
 [Vývoj řešení služby SharePoint](../sharepoint/developing-sharepoint-solutions.md)  
  