---
title: Karta System.Activities, zvolit položky panelu nástrojů – dialogové okno | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- VS.CHOOSEITEMS.SYSTEM.ACTIVITIES_COMPONENTS
- VS.CHOOSEITEMS.SYSTEM.ACTIVITIES COMPONENTS
ms.assetid: cef390cd-eeda-42e6-9d2e-18c8325a4f06
caps.latest.revision: 5
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: bed2df94edefdd074fab12244b93c032670f8cec
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49292042"
---
# <a name="systemactivities-tab-choose-toolbox-items-dialog-box"></a>Karta System.Activities, dialogové okno Zvolit položky panelu nástrojů
Této karty **zvolit položky nástrojů** dialogové okno zobrazí seznam [!INCLUDE[wf](../includes/wf-md.md)] aktivity, šablony a položky, které jsou k dispozici. Chcete-li zobrazit tento seznam, vyberte **zvolit položky nástrojů** z **nástroje** nabídky nebo kliknutím pravým tlačítkem myši **nástrojů** a vyberete **zvolit položky**zobrazíte **zvolit položky nástrojů** dialogové okno a pak vyberte jeho **System.Activities** kartu. Hned po spuštění obsahuje seznam aktivit pracovního postupu z System.Activities, System.ServiceModel.Activities a System.Activities.Core.Presentation sestavení; ale jenom poskytnuté systémem aktivity zobrazené a přidávají další sestavení zobrazí v **nástrojů** jsou ve výchozím nastavení zaškrtnuto. Naposledy přidané aktivity jsou automaticky zaškrtnuto a zobrazí se v **nástrojů** po kliknutí na **OK** v dialogovém okně. Navíc tyto položky se zobrazí v **nástrojů** pod novou kategorii, která odpovídá na obor názvů, ve které se nachází aktivity či položky nebo šablonu.  
  
> [!WARNING]
>  Pokud se pokusíte přidat sestavení, který neobsahuje žádné aktivity pracovního postupu, se zobrazí dialogové okno chyby, který vysvětluje, že sestavení neobsahuje žádné aktivity.  
  
 Toto dialogové okno je nezávislý na projekt a proto **System.Activities** kartu nadále zobrazí v samostatných XAML nebo typu projekt pracovního postupu.  
  
 Filtrování se provádí na každé kartě. To znamená, že není možné přidat aktivit pracovních postupů prostřednictvím **součásti .NET** kartu. Mají být přidány prostřednictvím **System.Activities** kartě samotný.  
  
 Můžete zrušit zaškrtnutí všech položek, které nechcete a podívejte se **nástrojů** z tohoto dialogového okna kartu, nebo Alternativně můžete k tomu použít **odstranit** možnost místní nabídky v **nástrojů** a zrušením odkazu na sestavení nedojde k odstranění položky z **nástrojů**.  
  
 Vytvoření instance aktivity, přetahováním myší v Návrháři přidá sestavení, který obsahuje položku do seznamu odkazovaných sestavení automaticky. Také pokud aktivity odkazuje na sestavení C, nepřidá C do seznamu odkazovaných sestavení. Sestavení C musí být v mezipaměti GAC nebo do stejného adresáře jako aktivita B. V případě samostatné sestavení musí být v GAC nebo cest test paměti VS. Teprve pak lze je přetáhnout myší aktivity na plochu návrháře pracovního postupu.  
  
 **Panel nástrojů** nastavení se ukládají ve výchozím nastavení jako uživatelské možnosti, proto příště, když otevřete **nástrojů**, zobrazí vaše vlastní seznam aktivit pracovního postupu. Jeden vedlejším účinkem této je, že pokud jste přidali položky konkrétní doménu k **nástrojů** prostřednictvím **zvolit položky nástrojů** dialogovém okně můžete i nadále vidět tyto položky při práci Konzolová aplikace pracovního postupu i. Pokud nechcete zobrazit, odstranit je pomocí místní nabídky nebo zrušte zaškrtnutí políčka je **zvolit položky nástrojů** dialogovému oknu, protože jste si poznamenali dříve.  
  
 Sloupce v tomto dialogovém obsahují následující informace:  
  
 Název  
 Obsahuje seznam aktivit pracovního postupu, které jsou aktuálně registrované na místním počítači.  
  
 Obor názvů  
 Zobrazuje hierarchii knihovna tříd rozhraní .NET Framework obor názvů, který definuje strukturu aktivity.  
  
 Název sestavení  
 Zobrazí název a verze sestavení rozhraní .NET Framework, který obsahuje aktivitu.  
  
 Adresář  
 Zobrazí umístění sestavení rozhraní .NET Framework, která obsahuje aktivity pracovního postupu. Je výchozím umístěním pro všechna sestavení do globální mezipaměti sestavení.  
  
 Součástí uvedené seřadit, vyberte libovolné záhlaví sloupce.