---
title: Přehled vícevrstvých datových aplikací
description: Přečíst N-vrstvou datovou aplikaci – přehled Také označované jako distribuované aplikace nebo vícevrstvé aplikace jsou datové aplikace rozdělené do mnoha vrstev.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: overview
helpviewer_keywords:
- presentation tier
- middle tier
- data tier
- n-tier applications, about n-tier applications
ms.assetid: 1020581d-eaaa-41a2-aca4-bf4c212895f6
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- data-storage
ms.openlocfilehash: c4a25cc340216e3410e0ca4b6cfabec77a73662e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99866681"
---
# <a name="n-tier-data-applications-overview"></a>Přehled vícevrstvých datových aplikací
*N-vrstvé* datové aplikace jsou datové aplikace, které jsou rozdělené do několika *vrstev*. Také označované jako "distribuované aplikace" a "vícevrstvé aplikace", n-vrstvé aplikace oddělují zpracování do diskrétních vrstev distribuovaných mezi klientem a serverem. Při vývoji aplikací s přístupem k datům by mělo být cíleno na rozdělení mezi různými úrovněmi, které aplikaci tvoří.

Typická n-vrstvá aplikace obsahuje prezentační vrstvu, střední vrstvu a datovou vrstvu. Nejjednodušším způsobem rozdělení různých vrstev v n-vrstvé aplikaci je vytvoření samostatných projektů pro každou úroveň, kterou chcete do aplikace zahrnout. Prezentační vrstvou může být například Formulářová aplikace Windows. Naproti tomu logikou přístupu k datům může být knihovna tříd, která je umístěna ve střední vrstvě. Prezentační vrstva navíc může komunikovat s logikou přístupu k datům v prostřední vrstvě prostřednictvím služby, jako je například webová služba. Rozdělení komponent aplikace do oddělených vrstev zvyšuje udržovatelnost a škálovatelnost aplikace. Je to dáno tím, že je umožněno snadnější přijímání nových technologií, které mohou být použity v jedné vrstvě, aniž by bylo nutné změnit návrh celého řešení. Kromě toho n-vrstvá aplikace obvykle ukládá citlivé informace do střední vrstvy, což zajišťuje izolaci od prezentační vrstvy.

Aplikace Visual Studio obsahuje několik funkcí, které usnadní vývojářům vytvářet n-vrstvé aplikace:

- Datová sada poskytuje vlastnost **projektu DataSet** , která umožňuje oddělit datovou sadu (datovou vrstvu) a objekty TableAdapter (Data Access Layer) do diskrétních projektů.

- [Nástroje LINQ to SQL v aplikaci Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md) poskytují nastavení pro generování třídy DataContext a datových tříd do samostatných oborů názvů. Tato skutečnost umožňuje logické rozdělení přístupu k datům a vrstev datové entity.

- [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index) poskytuje <xref:System.Data.Linq.Table%601.Attach%2A> metodu, která umožňuje spojování DataContext z různých vrstev v aplikaci. Další informace najdete v tématu [N-vrstvé a vzdálené aplikace s LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/n-tier-and-remote-applications-with-linq-to-sql).

## <a name="presentation-tier"></a>Prezentační úroveň
*Prezentační vrstva* je vrstva, ve které uživatelé komunikují s aplikací. Často také obsahuje další aplikační logiku. Mezi typické komponenty prezentační vrstvy patří:

- Komponenty datové vazby, jako je například <xref:System.Windows.Forms.BindingSource> a <xref:System.Windows.Forms.BindingNavigator>.

- Reprezentace objektu dat, například [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index) třídy entit pro použití v prezentační vrstvě.

Prezentační vrstva obvykle přistupuje k prostřední vrstvě pomocí odkazu na službu (například [Windows Communication Foundation služby a datové služby WCF v aplikaci Visual Studio](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md) ). Prezentační vrstva obvykle nepřistupuje přímo k datové vrstvě. Prezentační vrstva komunikuje s datovou vrstvou prostřednictvím součásti datového přístupu v rámci střední vrstvy.

## <a name="middle-tier"></a>Střední vrstva
*Střední vrstva* je vrstva, kterou prezentační vrstva a Datová vrstva používá ke vzájemné komunikaci. Mezi typické komponenty střední vrstvy patří:

- Obchodní logika, jako jsou obchodní pravidla a ověření dat.

- Komponenty datového přístupu a logiky, jako je například:

  - [Objekty TableAdapter](create-and-configure-tableadapters.md) a [dataadaptérs a datačtecís](/dotnet/framework/data/adonet/dataadapters-and-datareaders).

  - Objekt reprezentace dat, například [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index) třídy entit.

  - Běžné služby aplikací, jako je například ověření, autorizace a přizpůsobení.

Následující obrázek znázorňuje funkce a technologie, které jsou k dispozici v aplikaci Visual Studio a které je možné v rámci n-vrstvé aplikace umístit do střední vrstvy.

![Střední vrstva komponent střední vrstvy ](../data-tools/media/ntiermid.png)

Střední vrstva se obvykle připojuje k datové vrstvě pomocí datového připojení. Datové připojení je obvykle uloženo v komponentě datového přístupu.

## <a name="data-tier"></a>Datová vrstva
*Datová vrstva* je v podstatě Server, na kterém jsou uložena data aplikace (například server se systémem SQL Server).

Následující obrázek znázorňuje funkce a technologie, které jsou k dispozici v aplikaci Visual Studio a které je možné v rámci n-vrstvé aplikace umístit do datové vrstvy.

![Datová vrstva komponent datové vrstvy ](../data-tools/media/ntierdatatier.png)

K datové vrstvě nelze přistupovat přímo z klienta v prezentační vrstvě. Namísto toho je ke komunikaci mezi prezentační a datovou vrstvou použita komponenta datového přístupu ve střední vrstvě.

## <a name="help-for-n-tier-development"></a>Nápovědu pro vývoj na n-vrstvách
Následující témata obsahují informace o práci s n-vrstvými aplikacemi:

[Oddělení datových sad a objekty TableAdapter do různých projektů](../data-tools/separate-datasets-and-tableadapters-into-different-projects.md)

[Návod: Vytvoření n-vrstvých datových aplikací](../data-tools/walkthrough-creating-an-n-tier-data-application.md)

[N-vrstvé a vzdálené aplikace s LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/n-tier-and-remote-applications-with-linq-to-sql)

## <a name="see-also"></a>Viz také

- [Návod: Vytvoření n-vrstvých datových aplikací](../data-tools/walkthrough-creating-an-n-tier-data-application.md)
- [Hierarchická aktualizace](../data-tools/hierarchical-update.md)
- [Nástroje datových sad v sadě Visual Studio](../data-tools/dataset-tools-in-visual-studio.md)
- [Přístup k datům v sadě Visual Studio](../data-tools/accessing-data-in-visual-studio.md)
