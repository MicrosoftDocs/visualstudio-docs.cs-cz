---
title: Přizpůsobení chování při odstraňování | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
f1_keywords:
- vs.dsltools.dsldesigner.deletebehavior
helpviewer_keywords:
- Domain-Specific Language, deletion
ms.assetid: c6bf088d-52c6-4817-af45-ddae745bb5a9
caps.latest.revision: 25
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 9d0dcfc5724e87d57d2803b9b64a6eb121314b99
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72655047"
---
# <a name="customizing-deletion-behavior"></a>Přizpůsobení chování odstranění
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Odstranění elementu obvykle způsobí, že související prvky budou odstraněny také. Všechny relace, které jsou k němu připojené, a všechny podřízené prvky se odstraní. Toto chování se nazývá *Odstranit šíření*. Můžete přizpůsobit odstranění šíření, například pro uspořádání dalších souvisejících prvků, které jsou odstraněny. Zápisem kódu programu můžete vytvořit šíření v závislosti na stavu modelu. V reakci na odstranění můžete také způsobit další změny, které budou provedeny.

 Toto téma obsahuje následující oddíly:

- [Výchozí chování při odstraňování](#default)

- [Nastavení možnosti rozšíření pro odstranění role](#property)

- [Přepsání uzávěru odstranění](#closure) – tuto techniku použijte, pokud by odstranění mohlo vést k odstranění sousedních prvků.

- [Použití operací prodelete a IsDeleted](#ondeleting) – tyto metody můžete použít, pokud odpověď může zahrnovat jiné akce, jako je například aktualizace hodnoty uvnitř nebo vně obchodu.

- [Pravidla odstraňování](#rules) – pomocí pravidel můžete rozšířit aktualizace jakéhokoli druhu v rámci obchodu, kde jedna změna může vést k ostatním.

- [Události odstranění](#rules) – pomocí událostí úložiště můžete rozšířit aktualizace mimo úložiště, například na jiné dokumenty [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].

- [Unmerge](#unmerge) – pomocí operace zrušení sloučení vraťte operaci sloučení, která připojila podřízený element k nadřazenému elementu.

## <a name="default"></a>Výchozí chování při odstraňování
 Ve výchozím nastavení následující pravidla řídí odstranění šíření:

- Pokud je prvek odstraněn, jsou odstraněny také všechny vložené prvky. Vložené prvky jsou ty, které jsou cílem vložení vztahů, pro které je tento prvek zdrojem. Například pokud existuje vztah vložení z **alba** do **skladby**, pak při odstranění konkrétního alba se odstraní také všechny jeho skladby.

     Naproti tomu odstranění skladby neodstraní album.

- Ve výchozím nastavení odstranění nešíří podél referenčních vztahů. Pokud existuje referenční vztah **ArtistPlaysOnAlbum** z **alba** na **Interpret**, odstraněním alba nedojde k odstranění žádného souvisejícího interpreta a odstranění umělce neodstraní žádné album.

     Odstranění ale šíří společně některé předdefinované relace. Například při odstranění prvku modelu je také odstraněn jeho tvar v diagramu. Element a tvar souvisí s referenčním vztahem `PresentationViewsSubject`.

- Všechny relace, které jsou připojeny k elementu, buď na zdrojové nebo cílové roli, se odstraní. Vlastnost role elementu v opačné roli již neobsahuje odstraněný element.

## <a name="property"></a>Nastavení možnosti rozšíření pro odstranění role
 Může dojít k tomu, že odstranění se šíří podél referenčního vztahu nebo z vloženého podřízeného objektu k nadřazenému.

#### <a name="to-set-delete-propagation"></a>Nastavení odstranění šíření

1. V diagramu definice DSL vyberte *roli* , pro kterou chcete šíření odstranit. Role je reprezentovaná čárou na levé nebo pravé straně pole doménového vztahu.

    Například pokud chcete určit, že při každém odstranění alba jsou odstraněny také související interprety, pak vyberte roli připojenou k interpretovi třídy domény.

2. V okno Vlastnosti nastavte vlastnost rozšíření pro **odstranění** .

3. Stiskněte klávesu F5 a ověřte, že:

   - Když se odstraní instance této relace, odstraní se i element ve vybrané roli.

   - Při odstranění prvku u opačné role se instance této relace odstraní a související prvky v této roli se odstraní.

   V okně **Podrobnosti DSL** můžete také zobrazit možnost **rozšíření pro odstranění** . Vyberte doménovou třídu a v okně Podrobnosti DSL otevřete stránku **Odstranit chování** kliknutím na tlačítko na straně okna. Možnost **šířit** je zobrazena pro opačnou roli jednotlivých vztahů. Sloupec **Odstranit styl** označuje, zda je možnost **rozšířit** nastavena na výchozí nastavení, ale nemá žádný zvláštní efekt.

## <a name="delete-propagation-by-using-program-code"></a>Odstranit šíření pomocí kódu programu
 Možnosti v souboru definice DSL vám umožňují vybrat, jestli se odstraňování šíří do bezprostředního souseda. Chcete-li implementovat komplexnější schéma pro odstranění šíření, můžete napsat kód programu.

> [!NOTE]
> Chcete-li přidat kód programu do definice DSL, vytvořte samostatný soubor kódu v projektu **DSL** a zapište částečné definice pro rozšíření tříd ve vygenerované složce kódu. Další informace najdete v tématu [psaní kódu pro přizpůsobení jazyka specifického pro doménu](../modeling/writing-code-to-customise-a-domain-specific-language.md).

## <a name="closure"></a>Definování uzávěrky pro odstranění
 Operace odstranění používá třídu _YourModel_**DeleteClosure** k určení, které prvky se mají odstranit, a to s ohledem na počáteční výběr. Volá `ShouldVisitRelationship()` a `ShouldVisitRolePlayer()` opakovaně a přechází do grafu vztahů. Tyto metody můžete přepsat. ShouldVisitRolePlayer je k dispozici s identitou odkazu a elementu v jedné z rolí odkazu. Měla by vracet jednu z následujících hodnot:

- **VisitorFilterResult. Yes**– element by měl být smazán a prohlížeč by měl pokračovat v pokusech o další odkazy elementu.

- **VisitorFilterResult. DoNotCare** – element by neměl být smazán, pokud jiný dotaz neodpoví, že by měl být odstraněn.

- **VisitorFilterResult. Never** – element nesmí být odstraněn, i když jiný dotaz odpoví na **Ano**a prohlížeč by neměl vyzkoušet ostatní odkazy elementu.

```
// When a musician is deleted, delete their albums with a low rating.
// Override methods in <YourDsl>DeleteClosure in DomainModel.cs
partial class MusicLibDeleteClosure
{
  public override VisitorFilterResult ShouldVisitRolePlayer
    (ElementWalker walker, ModelElement sourceElement, ElementLink elementLink,
    DomainRoleInfo targetDomainRole, ModelElement targetRolePlayer)
  {
    ArtistAppearsInAlbum link = elementLink as ArtistAppearsInAlbum;
    if (link != null
       && targetDomainRole.RolePlayer.Id == Album.DomainClassId)
    {
      // Count other unvisited links to the Album of this link.
      if (ArtistAppearsInAlbum.GetLinksToArtists(link.Album)
              .Where(linkAlbumArtist =>
                     linkAlbumArtist != link &&
                     !walker.Visited(linkAlbumArtist))
              .Count() == 0)
      {
        // Should delete this role player:
        return VisitorFilterResult.Yes;
      }
      else
        // Don’t delete unless another relationship deletes it:
        return VisitorFilterResult.DoNotCare;
    }
    else
    {
      // Test for and respond to other relationships and roles here.

      // Not the relationship or role we’re interested in.
      return base.ShouldVisitRolePlayer(walker, sourceElement,
             elementLink, targetDomainRole, targetRolePlayer);
    }
  }
}

```

 Metoda uzavírání zajišťuje, že sada elementů a odkazů, které mají být odstraněny, je určena před zahájením odstraňování. Prohlížeč také kombinuje výsledky uzavření s ostatními částmi modelu.

 Nicméně technika předpokládá, že odstranění ovlivní pouze jeho okolí v grafu vztahů: tuto metodu nelze použít k odstranění elementu v jiné části modelu. Nemůžete jej použít, pokud chcete přidat prvky nebo provést jiné změny v reakci na odstranění.

## <a name="ondeleting"></a>Použití odstranění a odstranění
 @No__t_0 nebo `OnDeleted()` můžete přepsat buď v doménové třídě, nebo v doménovém vztahu.

1. <xref:Microsoft.VisualStudio.Modeling.ModelElement.OnDeleting%2A> se volá, když se bude element odstraňovat, ale před tím, než se jeho relace odpojí. Stále se naviguje do a z dalších prvků a je stále v `store.ElementDirectory`.

    Pokud je odstraněno několik prvků současně, je pro všechny z nich před provedením odstranění voláno odstranění.

    `IsDeleting` má hodnotu true.

2. <xref:Microsoft.VisualStudio.Modeling.ModelElement.OnDeleted%2A> se volá, když se element odstraní. Zůstane v haldě CLR, aby bylo možné provést vrácení zpět, je-li to nutné, ale není propojeno s jinými prvky a odebrán z `store.ElementDirectory`. U vztahů se role stále odkazují na staré aktéry rolí. `IsDeleted` má hodnotu true.

3. Odstranění a odstranění se volá, když uživatel vyvolá vrácení zpět po vytvoření elementu a když se předchozí odstranění opakuje znovu. Pomocí `this.Store.InUndoRedoOrRollback` se vyhnete aktualizaci prvků úložiště v těchto případech. Další informace naleznete v tématu [How to: use Transactions to Update a model](../modeling/how-to-use-transactions-to-update-the-model.md).

   Například následující kód odstraní album, když je odstraněna poslední podřízená skladba:

```

// Delete the parent Album when the last Song is deleted.
// Override methods in the embedding relationship between Album and Song:
partial class AlbumHasSongs
{
  protected override void OnDeleted()
  {
    base.OnDeleted();
    // Don't perform in-store actions in undo:
    if (this.Store.InUndoRedoOrRollback) return;
    // Relationship source and target still work:
    // Don't bother if source is already on its way out:
    if (!this.Album.IsDeleting && !this.Album.IsDeleted)
    {
      if (this.Album.Songs.Count == 0)
      {
        this.Album.Delete();
} } } }

```

 Je často užitečnější pro aktivaci z odstranění vztahu, než je element role, protože to funguje i při odstranění elementu a při odstranění vztahu samotného. V případě referenčního vztahu však můžete chtít rozšířit odstranění při odstranění souvisejícího prvku, ale ne v případě odstranění samotného vztahu. Tento příklad odstraní album, když je odstraněn jeho poslední přispívající Interpret, ale nereaguje, pokud jsou odstraněny relace:

```
using System.Linq; ...
// Assumes a many-many reference relationship
// between Artist and Album.
partial class Artist
{
  protected override void OnDeleting()
  {
    base.OnDeleting();
    if (this.Store.InUndoRedoOrRollback) return;
    List<Album> toDelete = new List<Album>();
    foreach (Album album in this.Albums)
    {
      if (album.Artists.Where(artist => !artist.IsDeleting)
                        .Count() == 0)
      {
        toDelete.Add(album);
      }
    }
    foreach (Album album in toDelete)
    {
      album.Delete();
} } }

```

 Při provádění <xref:Microsoft.VisualStudio.Modeling.ModelElement.Delete%2A> pro prvek, odstranění a odstranění se zavolá. Tyto metody jsou vždy prováděny jako vložené – to znamená bezprostředně před a po skutečném odstranění. Pokud váš kód odstraní dva nebo více prvků, odstranění a odstranění, budou volány v alternace pro všechny z nich.

## <a name="rules"></a>Pravidla odstraňování a události
 Jako alternativu k obslužným rutinám pro odstranění můžete definovat pravidla odstraňování a události odstranění.

1. Pravidla **odstraňování** a **odstraňování** se aktivují pouze v transakci, nikoli v operaci zpět nebo znovu. Můžete nastavit, aby byly zařazeny do fronty, aby je bylo možné provést na konci transakce, ve které je odstranění provedeno. Odstranění pravidel se vždycky spustí před všemi odstraněnými pravidly, která jsou ve frontě.

     Pomocí pravidel můžete rozšířit změny ovlivňující pouze prvky v úložišti, včetně vztahů, prvků diagramu a jejich vlastností. K šíření odstranění se obvykle používá pravidlo odstranění a pravidlo pro odstranění se používá k vytvoření náhradních prvků a vztahů.

     Další informace najdete v tématu [pravidla šířící změny v modelu](../modeling/rules-propagate-changes-within-the-model.md).

2. Událost **odstranění** úložiště je vyvolána na konci transakce a je volána po akci zpět nebo znovu. Dá se proto použít k šíření odstranění objektů mimo úložiště, jako jsou soubory, databázové položky nebo jiné objekty v [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].

     Další informace najdete v tématu [obslužné rutiny událostí rozšiřovat změny mimo model](../modeling/event-handlers-propagate-changes-outside-the-model.md).

    > [!WARNING]
    > Po odstranění elementu můžete získat přístup k hodnotám jeho doménových vlastností, ale nemůžete přejít na odkazy vztahů. Pokud jste však v relaci nastavili odstraněnou událost, můžete také přistupovat ke dvěma prvkům, které byly jeho aktéry role. Proto pokud chcete reagovat na odstranění prvku modelu, ale chcete získat přístup k prvku, ke kterému byl propojen, nastavte událost odstranění v relaci namísto třídy domény elementu modelu.

### <a name="example-deletion-rules"></a>Příklady pravidel odstranění

```
[RuleOn(typeof(Album), FireTime = TimeToFire.TopLevelCommit)]
internal class AlbumDeletingRule : DeletingRule
{
  public override void ElementDeleting(ElementDeletingEventArgs e)
  {
    base.ElementDeleting(e);
    // ...perform tasks to propagate imminent deletion
  }
}
[RuleOn(typeof(Album), FireTime = TimeToFire.TopLevelCommit)]
internal class AlbumDeletedRule : DeleteRule
{
  public override void ElementDeleted(ElementDeletedEventArgs e)
  {
    base.ElementDeleted(e);
    // ...perform tasks such as creating new elements
  }
}

// The rule must be registered:
public partial class MusicLibDomainModel
{
  protected override Type[] GetCustomDomainModelTypes()
  {
    List<Type> types = new List<Type>(base.GetCustomDomainModelTypes());
    types.Add(typeof(AlbumDeletingRule));
    types.Add(typeof(AlbumDeletedRule));
    // If you add more rules, list them here.
    return types.ToArray();
  }
}

```

### <a name="example-deleted-event"></a>Příklad odstraněné události

```
partial class NestedShapesSampleDocData
{
  protected override void OnDocumentLoaded(EventArgs e)
  {
    base.OnDocumentLoaded(e);
    DomainRelationshipInfo commentRelationship =
          this.Store.DomainDataDirectory
          .FindDomainRelationship(typeof(CommentsReferenceComponents));

    this.Store.EventManagerDirectory.ElementDeleted.Add(commentRelationship,
      new EventHandler<ElementDeletedEventArgs>(CommentLinkDeleted));
  }

  private void CommentLinkDeleted (object sender, ElementDeletedEventArgs e)
  {
    CommentsReferenceComponents link = e.ModelElement as CommentsReferenceComponents;
    Comment comment = link.Comment;
    Component component = link.Subject;
    if (comment.IsDeleted)
    {
      // The link was deleted because the comment was deleted.
      System.Windows.Forms.MessageBox.Show("Removed comment on " + component.Name);
    }
    else
    {
      // It was just the link that was deleted - the comment itself remains.
      System.Windows.Forms.MessageBox.Show("Removed comment link to "
           + component.Name);
    }
  }
}

```

## <a name="unmerge"></a>Zrušit sloučení
 Operace, která připojí podřízený element k nadřazenému elementu, se nazývá *Merge*. K tomu dojde při vytvoření nového prvku nebo skupiny prvků ze sady nástrojů nebo přesunutí z jiné části modelu nebo zkopírování ze schránky. Stejně jako vytvoření vztahu vložení mezi nadřazeným a novým podřízeným objektem může operace sloučení také nastavit další relace, vytvořit pomocné prvky a nastavit hodnoty vlastností v prvcích. Operace sloučení je zapouzdřena v direktivě sloučení elementů (EMD).

 EMD také zapouzdřuje doplňující operaci *odmerge* nebo `MergeDisconnect`. Pokud máte cluster prvků, které byly vytvořeny pomocí sloučení, je doporučeno použít přidružené zrušení sloučení pro odebrání elementu z něj, pokud chcete zbývající prvky ponechat v konzistentním stavu. Operace odslučování obvykle používá techniky popsané v předchozích částech.

 Další informace naleznete v tématu [přizpůsobení vytváření a přesunu prvku](../modeling/customizing-element-creation-and-movement.md).

## <a name="see-also"></a>Viz také
 [Přizpůsobení chování kopírování](../modeling/customizing-copy-behavior.md) [a přizpůsobení vytváření prvku a](../modeling/customizing-element-creation-and-movement.md) [psaní kódu pro přizpůsobení jazyka specifického pro doménu](../modeling/writing-code-to-customise-a-domain-specific-language.md)
