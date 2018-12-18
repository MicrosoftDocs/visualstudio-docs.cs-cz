---
title: Obslužné rutiny události šíří změny mimo model
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, programming domain models
- Domain-Specific Language, events
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: 02cf41daa9bea74e62ceb96f7c6227982bfcad84
ms.sourcegitcommit: 768d7877fe826737bafdac6c94c43ef70bf45076
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/02/2018
ms.locfileid: "50967347"
---
# <a name="event-handlers-propagate-changes-outside-the-model"></a>Obslužné rutiny události šíří změny mimo model

V produktu Visualization and Modeling SDK můžete definovat obslužné rutiny událostí úložiště změny na prostředky mimo úložiště, jako jsou proměnné bez úložiště, soubory, modely v jiných úložištích nebo jiné rozšíření sady Visual Studio. Obslužné rutiny událostí Store jsou spouštěny na konci transakce, ve kterém se aktivační událost došlo. Také se provádějí v operaci vrácení zpět nebo znovu. Proto se na rozdíl od úložiště pravidla jsou zvláště užitečná pro aktualizaci hodnoty, které jsou mimo store události v úložišti. Na rozdíl od .NET události jsou registrovány obslužné rutiny událostí úložiště tak, aby naslouchala na třídu: nemáte samostatnou obslužnou rutinu pro každou instanci zaregistrovat. Další informace o tom, jak si vybrat mezi různými způsoby pro případ změn najdete v tématu [šířící změny a reakce na](../modeling/responding-to-and-propagating-changes.md).

Grafické plochu a jiných prvcích uživatelského rozhraní jsou příkladem externí prostředky, které mohou být zpracovány události v úložišti.

### <a name="to-define-a-store-event"></a>Chcete-li definovat událost úložiště

1.  Vyberte typ události, ke které chcete monitorovat. Chcete-li zobrazit úplný seznam, podívejte se na vlastnosti <xref:Microsoft.VisualStudio.Modeling.EventManagerDirectory>. Každou vlastnost odpovídá typu události. Nejčastěji používané události, které typy jsou:

    -   `ElementAdded` -aktivuje, pokud prvek modelu, vztah odkazu, obrazec nebo spojnici se vytvoří.

    -   ElementPropertyChanged – aktivuje, když hodnota `Normal` doménovou vlastnost se změní. Událost se aktivuje jenom v případě, že novém i starém hodnoty nejsou shodné. Události nejde použít u vypočtené a vlastní vlastnosti úložiště.

         Ho nejde použít u vlastnosti rolí, které odpovídají vztah odkazy. Místo toho použijte `ElementAdded` monitorování doménového vztahu.

    -   `ElementDeleted` -aktivovat po prvku modelu, relace, obrazec nebo spojnici byl odstraněn. Budete k němu přístup hodnoty vlastností elementu, ale nebude mít žádné vztahy s ostatními prvky.

2.  Přidat definici částečné třídy pro _YourDsl_**DocData** v samostatném souboru kódu v **DslPackage** projektu.

3.  Psaní kódu události jako metody, jako v následujícím příkladu. Může to být `static`, pokud chcete získat přístup k `DocData`.

4.  Přepsat `OnDocumentLoaded()` zaregistrovat obslužnou rutinu. Pokud máte více než jednu obslužnou rutinu, můžete je zaregistrovat vše na jednom místě.

Umístění registrační kód není důležité. `DocView.LoadView()` je alternativního umístění.

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using Microsoft.VisualStudio.Modeling;

namespace Company.MusicLib
{
  partial class MusicLibDocData
  {
    // Register store events here or in DocView.LoadView().
    protected override void OnDocumentLoaded()
    {
      base.OnDocumentLoaded(); // Don't forget this.

      #region Store event handler registration.
      Store store = this.Store;
      EventManagerDirectory emd = store.EventManagerDirectory;
      DomainRelationshipInfo linkInfo = store.DomainDataDirectory
          .FindDomainRelationship(typeof(ArtistAppearsInAlbum));
      emd.ElementAdded.Add(linkInfo,
          new EventHandler<ElementAddedEventArgs>(AddLink));
      emd.ElementDeleted.Add(linkInfo,
          new EventHandler<ElementDeletedEventArgs>(RemoveLink));

      #endregion Store event handlers.
    }

    private void AddLink(object sender, ElementAddedEventArgs e)
    {
      ArtistAppearsInAlbum link = e.ModelElement as ArtistAppearsInAlbum;
      if (link != null)
            ExternalDatabase.Add(link.Artist.Name, link.Album.Title);
    }
    private void RemoveLink(object sender, ElementDeletedEventArgs e)
    {
      ArtistAppearsInAlbum link = e.ModelElement as ArtistAppearsInAlbum;
      if (link != null)
            ExternalDatabase.Delete(link.Artist.Name, link.Album.Title);
    }
  }
}
```

## <a name="use-events-to-make-undoable-adjustments-in-the-store"></a>Použití událostí s úpravami vrátit v Store

Store události nevyužívá obvykle pro šíření změn v úložišti, protože obslužná rutina události spustí poté, co je transakce potvrzena. Místo toho použijete pravidlo úložiště. Další informace najdete v tématu [pravidla šíření změn v rámci the Model](../modeling/rules-propagate-changes-within-the-model.md).

Ale můžete použít obslužnou rutinu události provést další aktualizace do úložiště, pokud má uživatel moci vrátit další aktualizace odděleně od původní událostí. Předpokládejme například, že malé znaky jsou běžné konvence pro alb. Můžete napsat obslužnou rutinu události úložiště, který opraví nadpis na malá písmena, poté, co uživatel má zadali velkými písmeny. Ale uživatel může pomocí příkazu Zpět Zrušit opravu, obnovení velká písmena. Druhý vrácení zpět by odeberte uživatele změnit.

Naopak pokud jste napsali úložiště pravidlo, které to samé udělá, změna uživatele a opravu by v rámci jedné transakce, tak, aby uživatel nelze vrátit zpět úpravy bez ztráty původní změny.

```csharp
partial class MusicLibDocView
{
    // Register store events here or in DocData.OnDocumentLoaded().
    protected override void LoadView()
    {
      /* Register store event handler for Album Title property. */
      // Get reflection data for property:
      DomainPropertyInfo propertyInfo =
        this.DocData.Store.DomainDataDirectory
        .FindDomainProperty(Album.TitleDomainPropertyId);
      // Add to property handler list:
      this.DocData.Store.EventManagerDirectory
        .ElementPropertyChanged.Add(propertyInfo,
        new EventHandler<ElementPropertyChangedEventArgs>
             (AlbumTitleAdjuster));

      /*
      // Alternatively, you can set one handler for
      // all properties of a class.
      // Your handler has to determine which property changed.
      DomainClassInfo classInfo = this.Store.DomainDataDirectory
           .FindDomainClass(typeof(Album));
      this.Store.EventManagerDirectory
          .ElementPropertyChanged.Add(classInfo,
        new EventHandler<ElementPropertyChangedEventArgs>
             (AlbumTitleAdjuster));
       */
      return base.LoadView();
    }

// Undoable adjustment after a property is changed.
// Method can be static since no local access.
private static void AlbumTitleAdjuster(object sender,
         ElementPropertyChangedEventArgs e)
{
  Album album = e.ModelElement as Album;
  Store store = album.Store;

  // We mustn't update the store in an Undo:
  if (store.InUndoRedoOrRollback
      || store.InSerializationTransaction)
      return;

  if (e.DomainProperty.Id == Album.TitleDomainPropertyId)
  {
    string newValue = (string)e.NewValue;
    string lowerCase = newValue.ToLowerInvariant();
    if (!newValue.Equals(lowerCase))
    {
      using (Transaction t = store.TransactionManager
            .BeginTransaction("adjust album title"))
      {
        album.Title = lowerCase;
        t.Commit();
      } // Beware! This could trigger the event again.
    }
  }
  // else other properties of this class.
}
```

Pokud píšete událost, která aktualizuje ve storu:

-   Použití `store.InUndoRedoOrRollback` vyhnout se provádění změn k prvkům modelu v vrácení zpět. Správce transakcí všechno, co nastavíte v úložišti zpět do původního stavu.

-   Použití `store.InSerializationTransaction` pro vyvarování změny při načítání modelu ze souboru.

-   Změny způsobí další události, které mají být aktivované. Ujistěte se, že byste se vyhnout nekonečnou smyčku.

## <a name="store-event-types"></a>Typy událostí Store

Každý typ události odpovídá kolekci v Store.EventManagerDirectory. Můžete přidat nebo odebrat obslužných rutin událostí v okamžiku, ale je obvykle při načtení dokumentu je přidat.

|`EventManagerDirectory` Název vlastnosti|Při spuštění|
|-|-|
|ElementAdded|Je vytvořena instance třídy domény, doménového vztahu, tvaru, konektoru nebo diagramu.|
|ElementDeleted|Prvek modelu se odebral z adresáře element obchodu a není už zdroj nebo cíl žádné relace. Prvku není odstraněn z paměti, ale se uchovávají v případě budoucího vrácení zpět.|
|ElementEventsBegun|Vyvolána na konci vnější transakci.|
|ElementEventsEnded|Vyvoláno, když všechny další události byly zpracovány.|
|ElementMoved|Prvek modelu bylo přesunuto z jednoho úložiště pro oddíl do jiného.<br /><br /> To se nevztahuje k umístění obrazec v diagramu.|
|ElementPropertyChanged|Hodnota doménová vlastnost, která se změnila. Provádí pouze v případě, že staré a nové hodnoty rovny.|
|RolePlayerChanged|Jednu ze dvou rolí (končí) vztah odkazuje na nový prvek.|
|RolePlayerOrderChanged|V roli s násobností větší než 1 došlo ke změně pořadí odkazů.|
|TransactionBeginning||
|TransactionCommitted||
|TransactionRolledBack||

## <a name="see-also"></a>Viz také

- [Reagování na změny a šíření změn](../modeling/responding-to-and-propagating-changes.md)
- [Ukázkový kód: diagramy okruh](https://code.msdn.microsoft.com/Visualization-Modeling-SDK-763778e8)

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]