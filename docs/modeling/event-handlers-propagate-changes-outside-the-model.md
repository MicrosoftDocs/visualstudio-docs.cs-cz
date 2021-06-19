---
title: Obslužné rutiny události šíří změny mimo model
description: Přečtěte si, že v sadě pro vizualizaci a modelování můžete definovat obslužné rutiny událostí úložiště pro rozšíření změn prostředků mimo úložiště.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, programming domain models
- Domain-Specific Language, events
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 115d26840f321792712392367794e443e41543a2
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/19/2021
ms.locfileid: "112388942"
---
# <a name="event-handlers-propagate-changes-outside-the-model"></a>Obslužné rutiny události šíří změny mimo model

V sadě pro vizualizaci a modelování můžete definovat obslužné rutiny událostí úložiště pro rozšíření změn prostředků mimo úložiště, jako jsou proměnné, soubory, modely v jiných úložištích nebo jiná rozšíření sady Visual Studio. Obslužné rutiny události úložiště se spouštějí po konci transakce, ve které došlo k aktivované události. Jsou také spouštěny v operaci zpět nebo znovu. Proto na rozdíl od pravidel úložiště jsou události úložiště nejužitečnější pro aktualizaci hodnot, které jsou mimo úložiště. Na rozdíl od událostí .NET jsou obslužné rutiny událostí úložiště registrovány pro naslouchání třídě: nemusíte registrovat samostatnou obslužnou rutinu pro každou instanci. Další informace o tom, jak volit mezi různými způsoby zpracování změn, najdete v tématu [reakce na a šíření změn](../modeling/responding-to-and-propagating-changes.md).

Grafické a jiné ovládací prvky uživatelského rozhraní jsou příklady externích prostředků, které mohou být zpracovány pomocí událostí úložiště.

### <a name="to-define-a-store-event"></a>Definování události úložiště

1. Vyberte typ události, kterou chcete monitorovat. Úplný seznam naleznete v části vlastnosti <xref:Microsoft.VisualStudio.Modeling.EventManagerDirectory> . Každá vlastnost odpovídá typu události. Nejčastěji používané typy událostí jsou:

    - `ElementAdded` -aktivováno při vytvoření prvku modelu, propojení relace, tvaru nebo spojnici.

    - ElementPropertyChanged – aktivuje se při `Normal` změně hodnoty vlastnosti domény. Událost se aktivuje jenom v případě, že se nové a staré hodnoty neshodují. Událost nelze použít pro počítané a vlastní vlastnosti úložiště.

         Nedá se použít na vlastnosti role, které odpovídají odkazům na vztahy. Místo toho použijte `ElementAdded` k monitorování doménového vztahu.

    - `ElementDeleted` -aktivováno po odstranění prvku modelu, vztahu, tvaru nebo konektoru. Můžete mít stále přístup k hodnotám vlastností elementu, ale nebude mít žádný vztah k ostatním elementům.

2. Přidejte definici částečné třídy pro _YourDsl_**DocData** do samostatného souboru kódu v projektu **DslPackage** .

3. Napište kód události jako metodu, jak je uvedeno v následujícím příkladu. Může to být `static` , pokud nechcete mít přístup `DocData` .

4. Přepište `OnDocumentLoaded()` pro registraci obslužné rutiny. Pokud máte více než jednu obslužnou rutinu, můžete je zaregistrovat na stejném místě.

Umístění registračního kódu není kritické. `DocView.LoadView()` je alternativní umístění.

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

## <a name="use-events-to-make-undoable-adjustments-in-the-store"></a>Použití událostí k provedení nevratných úprav v úložišti

Události úložiště se obvykle nepoužívají pro rozšiřování změn v úložišti, protože se obslužná rutina události spustí po potvrzení transakce. Místo toho byste použili pravidlo obchodu. Další informace najdete v tématu [pravidla šířící změny v modelu](../modeling/rules-propagate-changes-within-the-model.md).

Můžete však použít obslužnou rutinu události k provedení dalších aktualizací úložiště, pokud chcete, aby uživatel mohl vrátit další aktualizace odděleně od původní události. Předpokládejme například, že malá písmena představují obvyklou konvenci pro názvy alb. Můžete napsat obslužnou rutinu události úložiště, která opravuje nadpis na malý případ poté, co ho uživatel zadal velkými písmeny. Ale uživatel může použít příkaz zpět k zrušení opravy a obnovení velkých písmen. Druhý příkaz zpět by odebral změnu uživatele.

Naproti tomu, pokud jste napsali pravidlo obchodu ke stejnému účelu, změna uživatele a vaše Oprava by byly ve stejné transakci, aby uživatel nemohli zrušit úpravu bez ztráty původní změny.

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

Pokud napíšete událost, která aktualizuje úložiště:

- Použijte `store.InUndoRedoOrRollback` k tomu, abyste se vyhnuli provádění změn v prvcích modelu vrácení zpět. Správce transakcí nastaví vše ve Storu zpátky do původního stavu.

- Použijte `store.InSerializationTransaction` k zamezení provádění změn v průběhu načítání modelu ze souboru.

- Změny způsobí aktivaci dalších událostí. Ujistěte se, že se vyhnete nekonečné smyčce.

## <a name="store-event-types"></a>Typy událostí úložiště

Každý typ události odpovídá kolekci v úložišti. EventManagerDirectory. Obslužné rutiny událostí můžete kdykoli přidat nebo odebrat, ale při načtení dokumentu je obvykle můžete přidat.

|`EventManagerDirectory` Název vlastnosti|Spustí se, když|
|-|-|
|ElementAdded|Vytvoří se instance doménové třídy, doménového vztahu, obrazce, spojnice nebo diagramu.|
|ElementDeleted|Prvek modelu byl odebrán z adresáře prvků úložiště a již není zdrojem ani cílem žádného vztahu. Prvek není ve skutečnosti odstraněný z paměti, ale je uložený v případě budoucího vrácení akce zpět.|
|ElementEventsBegun|Vyvoláno na konci vnější transakce.|
|ElementEventsEnded|Vyvoláno při zpracování všech ostatních událostí.|
|ElementMoved|Prvek modelu byl přesunut z jednoho oddílu úložiště do druhého.<br /><br /> Nesouvisí s umístěním tvaru v diagramu.|
|ElementPropertyChanged|Hodnota doménové vlastnosti se změnila. Tato hodnota je provedena pouze v případě, že staré a nové hodnoty nejsou stejné.|
|RolePlayerChanged|Jedna ze dvou rolí (končí) vztahu odkazuje na nový prvek.|
|RolePlayerOrderChanged|V roli s násobností větší než 1 se změnila posloupnost odkazů.|
|TransactionBeginning||
|TransactionCommitted||
|TransactionRolledBack||

## <a name="see-also"></a>Viz také

- [Reagování na změny a šíření změn](../modeling/responding-to-and-propagating-changes.md)
- [Vzorový kód: diagramy okruhů](https://code.msdn.microsoft.com/Visualization-Modeling-SDK-763778e8)

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]
