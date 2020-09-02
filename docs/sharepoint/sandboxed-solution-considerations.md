---
title: Otázky řešení v izolovaném prostoru | Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.Project.SandboxedSolutions
- VS.SharePointTools.Security.SandboxedSolutions
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, sandboxed solutions
- sandboxed solutions [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, farm solutions
- farm solutions [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 3f6345e7627549c672aa28fac8cba5f6d9658a23
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "64793817"
---
# <a name="sandboxed-solution-considerations"></a>Otázky řešení v izolovaném prostoru
  *Řešení v izolovaném prostoru* jsou funkce služby Microsoft SharePoint 2010, která umožňuje uživatelům kolekce webů nahrávat vlastní řešení pro kód. Společné řešení v izolovaném prostoru (sandbox) ukládá uživatelům své vlastní Webové části.

 Aplikace SharePoint v izolovaném prostoru běží v zabezpečeném monitorovaném procesu, který má přístup k omezené části webové farmy. Microsoft SharePoint 2010 používá kombinaci funkcí, galerií řešení, monitorování řešení a ověřovacího rozhraní pro povolení řešení v izolovaném prostoru.

## <a name="specify-project-trust-level"></a>Zadat úroveň důvěryhodnosti projektu
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] podporuje řešení v izolovaném prostoru prostřednictvím logické vlastnosti projektu nazývané *řešení v izolovaném prostoru (sandbox)*. Tuto vlastnost lze nastavit kdykoli v projektu nebo ji lze zadat při vytváření projektu v **Průvodci vlastním nastavením služby SharePoint**.

> [!NOTE]
> Změna vlastnosti *řešení v izolovaném prostoru* projektu po jeho vytvoření může způsobit chyby ověřování.

 Řešení je považováno za řešení v oboru farmy, pokud je vlastnost *řešení v izolovaném prostoru* nastavena na **hodnotu false** nebo pokud zvolíte možnost **nasadit jako řešení farmy** . Řešení se však zpracovává jinak než řešení farmy, pokud je vlastnost *řešení v izolovaném prostoru* nastavena na **hodnotu true** nebo pokud v průvodci zvolíte možnost **nasadit jako řešení v izolovaném prostoru** .

## <a name="sharepoint-site-hierarchy"></a>Hierarchie webu služby SharePoint
 Abychom pochopili, jak řešení v izolovaném prostoru fungují, pomáhá vědět, že jsou weby služby SharePoint hierarchické v oboru. Nejvyšší prvek je označován jako webová farma a další prvky jsou podřízeny:

 Webová farma

 Webová aplikace A

 Kolekce webů a1

 A1a webu

 Webová aplikace B

 Kolekce webů B1

 B1a webu

 B1b webu

 Kolekce webů B2

 B2a webu

 Jak vidíte, webové farmy mohou obsahovat jednu nebo více webových aplikací, které mohou obsahovat jednu nebo více kolekcí webů, které mohou mít podřízené lokality atd. Změny provedené v jedné kolekci webů ovlivňují pouze tuto kolekci webů a žádné jiné. Změny provedené na úrovni webové farmy mají ale vliv na všechny kolekce webů ve farmě.

 Služba Windows SharePoint Services (WSS) 3,0 umožňuje nasadit řešení pouze do úrovně farmy, ale [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] umožňuje nasazení na úrovni farmy (řešení farmy) nebo na úrovni kolekce webů (řešení v izolovaném prostoru).

## <a name="why-sandboxed-solutions"></a>Proč řešení v izolovaném prostoru?
 Ve WSS 3,0 se řešení mohla nasadit jenom na úroveň farmy. To znamenalo, že by mohla být nasazena potenciálně škodlivá nebo destabilizující řešení, která ovlivnila celou webovou farmu a všechny další kolekce webů a aplikace, které jsou v ní spuštěné. Nicméně pomocí řešení v izolovaném prostoru můžete nasadit vaše řešení do dílčí oblasti farmy, konkrétní kolekce webů. Pro zajištění další ochrany není sestavení řešení načteno do hlavního [!INCLUDE[TLA2#tla_iis5](../sharepoint/includes/tla2sharptla-iis5-md.md)] procesu (*w3wp.exe*). Místo toho je načten do samostatného procesu (*SPUCWorkerProcess.exe*). Tento proces se monitoruje a implementuje kvóty a omezování pro ochranu farmy z řešení v izolovaném prostoru, které provádí škodlivé aktivity, jako je spouštění těsných smyček využívajících cykly procesoru.

## <a name="site-collection-solution-gallery"></a>Galerie řešení kolekce webů
 [!INCLUDE[sharepointShort](../sharepoint/includes/sharepointshort-md.md)] 2010 má funkci, která se nazývá galerie řešení kolekce webů. K této funkci můžete přistupovat ze stránky centrální správy SharePoint 2010 nebo otevřením nabídky **Akce webu** , volbou možnosti **nastavení lokality**a následným výběrem odkazu **řešení** v části  **Galerie** na webu služby SharePoint. Galerie řešení jsou úložiště řešení, která správcům kolekce webů umožňují spravovat řešení v kolekcích webů.

 Galerie řešení je knihovna dokumentů uložená na kořenovém webu webu služby SharePoint. Galerie řešení nahrazuje šablony webů a podporuje balíčky řešení. Když se nahraje soubor balíčku řešení SharePoint (*. wsp*), zpracuje se jako řešení v izolovaném prostoru (sandbox).

## <a name="sandboxed-solution-limitations"></a>Omezení řešení v izolovaném prostoru
 Po nasazení řešení v izolovaném prostoru je pole funkcí SharePointu, které je k dispozici, omezené, aby bylo možné snížit případné chyby zabezpečení, které může mít. Mezi tato omezení patří následující:

- Řešení v izolovaném prostoru mají k dispozici omezené podmnožiny nasazených prvků řešení. Potenciálně zranitelné šablony projektu služby SharePoint, jako jsou definice webu a pracovní postupy, nejsou k dispozici.

- Služba SharePoint spouští kód řešení v izolovaném prostoru v procesu (*SPUCWorkerProcess.exe*) oddělený od [!INCLUDE[TLA2#tla_iis5](../sharepoint/includes/tla2sharptla-iis5-md.md)] procesu hlavního fondu aplikací (*w3wp.exe*).

- Mapované složky nelze do projektu přidat.

- Typy v [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] sestavení Microsoft. Office. Server se nedají použít v řešeních v izolovaném prostoru. [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)]V řešeních v izolovaném prostoru lze také použít pouze typy v sestavení Microsoft. SharePoint.

  Je důležité si uvědomit, že zadání řešení služby SharePoint jako řešení v izolovaném prostoru nemá žádné vliv na SharePoint Server; pouze určuje, jak je projekt služby SharePoint nasazen do služby SharePoint z [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] a jaká sestavení se váže k. Nemá vliv na vygenerovaný soubor *. wsp* a soubor *. wsp* neobsahuje žádná data, která přímo koreluje s vlastností řešení v *izolovaném prostoru* .

## <a name="capabilities-and-elements-in-sandboxed-solutions"></a>Možnosti a prvky v řešeních v izolovaném prostoru
 Řešení v izolovaném prostoru podporují následující funkce a prvky:

- Typy obsahu/pole

- Vlastní akce

- Deklarativní pracovní postupy

- Přijímače událostí

- Popisky funkcí

- Definice seznamu

- Instance seznamů

- Modul/soubory

- Navigace

- *Onet.xml*

- SPItemEventReceiver

- SPListEventReceiver

- SPWebEventReceiver

- Podpora pro všechny Webové části odvozené od `System.Web.UI.WebControls.WebParts.WebPart`

- Webové části

- Prvky funkce webtemplate (místo *Webtemp.xml*)

- Vizuální Webové části

  Řešení v izolovaném prostoru nepodporují následující funkce a prvky:

- Stránky aplikace

- Vlastní skupina akcí

- Funkce v oboru farmy

- `HideCustomAction` – element

- Funkce v oboru webové aplikace

- Pracovní postupy s kódem

## <a name="see-also"></a>Viz také
- [Rozdíly mezi řešeními v izolovaném prostoru a farmách](../sharepoint/differences-between-sandboxed-and-farm-solutions.md)
- [Vývoj řešení služby SharePoint](../sharepoint/developing-sharepoint-solutions.md)
