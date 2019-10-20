---
title: Přehled N-vrstvých datových aplikací | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- presentation tier
- middle tier
- data tier
- n-tier applications, about n-tier applications
ms.assetid: 1020581d-eaaa-41a2-aca4-bf4c212895f6
caps.latest.revision: 29
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 0f124e997669370e71819cf37423d0c2d6a414d7
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72658060"
---
# <a name="n-tier-data-applications-overview"></a>Přehled vícevrstvých datových aplikací
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Datové aplikace pro N-vrstvé * jsou datové aplikace, které jsou rozdělené do několika *vrstev*. Nazývají se také „distribuované aplikace“ a „vícevrstvé aplikace“. N-vrstvé aplikace oddělují zpracování do samostatných vrstev, které jsou distribuovány mezi klientem a serverem. Při vývoji aplikací s přístupem k datům by mělo být cíleno na rozdělení mezi různými úrovněmi, které aplikaci tvoří.

 Typická n-vrstvá aplikace obsahuje prezentační vrstvu, střední vrstvu a datovou vrstvu. Nejjednodušším způsobem rozdělení různých vrstev v n-vrstvé aplikaci je vytvoření samostatných projektů pro každou úroveň, kterou chcete do aplikace zahrnout. Prezentační vrstvou může být například Formulářová aplikace Windows. Naproti tomu logikou přístupu k datům může být knihovna tříd, která je umístěna ve střední vrstvě. Prezentační vrstva může navíc komunikovat s logikou přístupu dat ve střední vrstvě prostřednictvím služby. Rozdělení komponent aplikace do oddělených vrstev zvyšuje udržovatelnost a škálovatelnost aplikace. Je to dáno tím, že je umožněno snadnější přijímání nových technologií, které mohou být použity v jedné vrstvě, aniž by bylo nutné změnit návrh celého řešení. Kromě toho n-vrstvá aplikace obvykle ukládá citlivé informace do střední vrstvy, což zajišťuje izolaci od prezentační vrstvy.

 Aplikace Visual Studio obsahuje několik funkcí, které usnadní vývojářům vytvářet n-vrstvé aplikace:

- Návrhář DataSet poskytuje vlastnost **projektu DataSet** , která umožňuje oddělit datovou sadu (datovou vrstvu) a `TableAdapter`s (Data Access Layer) do diskrétních projektů.

- [Nástroje LINQ to SQL v aplikaci Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md) poskytují nastavení pro generování třídy DataContext a datových tříd do samostatných oborů názvů. Tato skutečnost umožňuje logické rozdělení přístupu k datům a vrstev datové entity.

- [LINQ to SQL](https://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655) poskytuje metodu <xref:System.Data.Linq.Table%601.Attach%2A>, která umožňuje spojování kontextu DataContext z různých vrstev v aplikaci. Další informace najdete v tématu [N-vrstvé a vzdálené aplikace s LINQ to SQL](https://msdn.microsoft.com/library/854a1cdd-53cb-45f5-83ca-63962a9b3598).

## <a name="presentation-tier"></a>Prezentační vrstva
 *Prezentační vrstva* je vrstva, ve které uživatelé komunikují s aplikací. Často také obsahuje další aplikační logiku. Mezi typické komponenty prezentační vrstvy patří:

- Komponenty datové vazby, jako je například <xref:System.Windows.Forms.BindingSource> a <xref:System.Windows.Forms.BindingNavigator>.

- Reprezentace objektu dat, například [LINQ to SQL](https://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655) třídy entit pro použití v prezentační vrstvě.

  Prezentační vrstva obvykle přistupuje k prostřední vrstvě pomocí odkazu na službu (například [Windows Communication Foundation služby a WCF Data Services v aplikaci Visual Studio](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md) ). Prezentační vrstva obvykle nepřistupuje přímo k datové vrstvě. Prezentační vrstva komunikuje s datovou vrstvou prostřednictvím součásti datového přístupu v rámci střední vrstvy.

## <a name="middle-tier"></a>Střední vrstva
 *Střední vrstva* je vrstva, kterou prezentační vrstva a Datová vrstva používá ke vzájemné komunikaci. Mezi typické komponenty střední vrstvy patří:

- Obchodní logika, jako jsou obchodní pravidla a ověření dat.

- Komponenty datového přístupu a logiky, jako je například:

  - [Objekty TableAdapter](https://msdn.microsoft.com/library/09416de9-134c-4dc7-8262-6c8d81e3f364) a [dataadaptérs a datačtecís](https://msdn.microsoft.com/library/cc952ca2-ec19-46ab-9189-15174b52cb74).

  - Objekt reprezentace dat, například [LINQ to SQL](https://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655) třídy entit.

  - Běžné služby aplikací, jako je například ověření, autorizace a přizpůsobení.

  Následující obrázek znázorňuje funkce a technologie, které jsou k dispozici v aplikaci Visual Studio a které je možné v rámci n-vrstvé aplikace umístit do střední vrstvy.

  ![Komponenty střední vrstvy](../data-tools/media/ntiermid.png "NtierMid") Střední vrstva

  Střední vrstva se obvykle připojuje k datové vrstvě pomocí datového připojení. Datové připojení je obvykle uloženo v komponentě datového přístupu.

## <a name="data-tier"></a>Datová vrstva
 *Datová vrstva* je v podstatě Server, na kterém jsou uložena data aplikace (například server se systémem [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]).

 Následující obrázek znázorňuje funkce a technologie, které jsou k dispozici v aplikaci Visual Studio a které je možné v rámci n-vrstvé aplikace umístit do datové vrstvy.

 ![Komponenty datové vrstvy](../data-tools/media/ntierdatatier.png "ntierdatatier") Datová vrstva

 K datové vrstvě nelze přistupovat přímo z klienta v prezentační vrstvě. Namísto toho je ke komunikaci mezi prezentační a datovou vrstvou použita komponenta datového přístupu ve střední vrstvě.

## <a name="help-for-n-tier-development"></a>Nápověda pro N-vrstvý vývoj
 Následující témata obsahují informace o práci s n-vrstvými aplikacemi:

 [Rozdělování datových sad a objektů TableAdapter do různých projektů](../data-tools/separate-datasets-and-tableadapters-into-different-projects.md)

 [Návod: Vytvoření vícevrstvé datové aplikace](../data-tools/walkthrough-creating-an-n-tier-data-application.md)

 [Návod: Přidání ověřování do N-vrstvých datových aplikací](https://msdn.microsoft.com/library/b35d072c-31f0-49ba-a225-69177592c265)

 [N-vrstvé a vzdálené aplikace s LINQ to SQL](https://msdn.microsoft.com/library/854a1cdd-53cb-45f5-83ca-63962a9b3598)

## <a name="see-also"></a>Viz také
 <xref:System.Data.Linq.ITable.Attach%2A> [Návod: vytvoření struktury N-vrstvých datových aplikací](../data-tools/walkthrough-creating-an-n-tier-data-application.md) [](../data-tools/hierarchical-update.md) [v sadě Visual Studio](../data-tools/dataset-tools-in-visual-studio.md) [přístup k datům v sadě Visual Studio](../data-tools/accessing-data-in-visual-studio.md)
