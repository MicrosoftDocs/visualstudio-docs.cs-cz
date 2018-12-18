---
title: Přizpůsobení chování odstranění
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.dsltools.dsldesigner.deletebehavior
helpviewer_keywords:
- Domain-Specific Language, deletion
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: a4b3df4661b23268fed811799c80cfc31b624a50
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49849148"
---
# <a name="customizing-deletion-behavior"></a>Přizpůsobení chování odstranění
Odstranění elementu obvykle způsobí, že související prvky také odstranit. Všechny vztahy, jsou k němu připojená, a odstraní se všechny podřízené prvky. Toto chování je s názvem *odstranit šíření*. Můžete přizpůsobit šíření operace delete, třeba zajistit, že další související prvky jsou odstraněny. Napsáním kódu programu, můžete provést odstranění šíření závisí na stavu modelu. Další změny v reakci na odstranění může také způsobit.

 Toto téma obsahuje následující oddíly:

-   [Výchozí chování při odstranění](#default)

-   [Nastavení možnosti šířit odstranit role](#property)

-   [Přepsání odstranit uzavření](#closure) – tento postup použít, kde odstranění může vést k odstranění sousedních elementy.

-   [Pomocí OnDeleting a OnDeleted](#ondeleting) -používat tyto metody, kde odpověď může obsahovat další akce, jako je aktualizace hodnotu uvnitř nebo mimo úložiště.

-   [Odstranění pravidla](#rules) -použít pravidla k šíření aktualizací jakéhokoli druhu v rámci úložiště, kde by mohly vést jednu změnu ostatním uživatelům.

-   [Odstranění událostí](#rules) – události v úložišti použití k šíření aktualizací mimo úložiště, například další dokumenty, které Visual Studio.

-   [Oddělit](#unmerge) -použít oddělit operace vrátit zpět operaci sloučení, který je připojen podřízený element svého nadřazeného objektu.

## <a name="default"></a> Výchozí chování při odstranění
 Ve výchozím nastavení platí následující pravidla šíření odstranit:

-   Pokud element se odstraní, odstraní se také všechny vložené prvky. Vložené prvky jsou ty, které jsou cíle relace, pro které tento element má zdroj vkládání. Například, pokud existuje vztah obsažení z **alba** k **skladby**, pak při odstranění určité Album se odstraní také všechny jeho skladeb.

     Naopak odstraněním určité skladby nedojde k odstranění alba.

-   Ve výchozím nastavení odstranění nešíří podél referenční stavy. Pokud existuje vztah odkazu **ArtistPlaysOnAlbum** z **alba** k **interpreta**, odstraněním alba nedojde k odstranění všech souvisejících interpreta, a odstraňuje umělce není Odstraňte všechny album.

     Odstranění však rozšířit podél některé předdefinované vztahy. Například při odstranění prvku modelu, jeho tvar v diagramu je také odstranit. Element a tvar se vztahují `PresentationViewsSubject` odkazovat na relaci.

-   Odstranění všech relací, který je připojen k elementu, buď na zdrojová nebo cílová role. Vlastnosti role elementu v opačné role už neobsahuje odstraněného elementu.

## <a name="property"></a> Nastavení možnosti šířit odstranit role
 Může způsobit odstranění rozšíření podél vztah odkazu nebo z vložené podřízené k nadřazené úloze.

#### <a name="to-set-delete-propagation"></a>Chcete-li nastavit šíření delete

1. V definici DSL diagramu, vyberte *role* na který chcete odstranit šíření. Role je reprezentován řádku nalevo nebo napravo od pole vztah domény.

    Například pokud chcete určit, že pokaždé, když se odstraní alba, související umělci se také odstraní a potom vyberte role připojen k doménové třídy interpreta.

2. V okně Vlastnosti nastavte **šíří odstranit** vlastnost.

3. Stiskněte klávesu F5 a ověřte, že:

   -   Při odstranění instance tohoto vztahu se budou odstraněny také element na vybranou roli.

   -   Když se odstraní prvek na opačné role, výskyty tento vztah se odstraní a související prvky na této role budou odstraněny.

   Můžete zobrazit také **šíří odstranit** možnost **podrobnosti DSL** okna. Vyberte doménové třídy a v okně podrobností DSL, otevřete **chování odstranění** stránku kliknutím na tlačítko na okraji okna. **Rozšířit** opačné role každé relaci se zobrazí možnost. **Odstranit styl** sloupec označuje, zda **rozšířit** na jeho výchozí nastavení je možnost, ale nemá žádný účinek samostatné.

## <a name="delete-propagation-by-using-program-code"></a>Odstranit šíření pomocí kódu programu
 Možnosti v souboru definic DSL pouze si můžete zvolit, jestli odstranění šíří do sousedního okamžitě. K implementaci složitější schéma šíření odstranit, můžete napsat kód programu.

> [!NOTE]
>  Přidat programový kód do definice DSL vytvořením samostatném souboru kódu v **Dsl** projektu a zapsat Částečná definice pro rozšíření třídy ve složce vygenerovaném kódu. Další informace najdete v tématu [psaní kódu pro úpravu jazyka specifického pro doménu specifického](../modeling/writing-code-to-customise-a-domain-specific-language.md).

## <a name="closure"></a> Definování uzavření Delete
 Operace odstranění používá třídu _YourModel_**DeleteClosure** určit prvky, které chcete odstranit, zadaný počáteční výběr. Volá `ShouldVisitRelationship()` a `ShouldVisitRolePlayer()` opakovaně, procházení grafu relací. Můžete také přepsat tyto metody. ShouldVisitRolePlayer je součástí identity odkazu a element v jedné z rolí na odkaz. Měla by vrátit jednu z následujících hodnot:

-   **VisitorFilterResult.Yes**– element by se měla odstranit a pokračovat walker vyzkoušet další odkazy na elementu.

-   **VisitorFilterResult.DoNotCare** -element se nesmí odstranit, pokud jiný dotaz, odpoví, že je nutné ji odstranit.

-   **VisitorFilterResult.Never** – prvek nesmí být odstraněno, i v případě, že jiný dotaz, odpoví **Ano**, a walker, neměli by zkoušet elementu je další odkazy.

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
        // Don't delete unless another relationship deletes it:
        return VisitorFilterResult.DoNotCare;
    }
    else
    {
      // Test for and respond to other relationships and roles here.

      // Not the relationship or role we're interested in.
      return base.ShouldVisitRolePlayer(walker, sourceElement,
             elementLink, targetDomainRole, targetRolePlayer);
    }
  }
}
```

 Uzavření postup zajistí, že se před zahájením odstranění určuje sadu elementů a odkazy na odstranit. Walker také kombinuje výsledky vašich uzavření s uživateli z jiných částí modelu.

 Ale postup předpokládá, že odstranění ovlivňuje pouze jeho okolím v grafu relací: pomocí této metody nelze odstranit prvek v jiné části modelu. Jej nelze použít, pokud chcete přidat prvky nebo provést další změny v reakci na odstranění.

## <a name="ondeleting"></a> Pomocí OnDeleting a OnDeleted
 Můžete přepsat `OnDeleting()` nebo `OnDeleted()` buď v doménové třídy, nebo doménového vztahu.

1. <xref:Microsoft.VisualStudio.Modeling.ModelElement.OnDeleting%2A> je volána element blížící se neodstraní, ale před jeho vztahy byl odpojen. Je stále navigaci do a z dalších prvků a je pořád ještě v `store.ElementDirectory`.

    Pokud několik prvků jsou odstraněny ve stejnou dobu, se nazývá OnDeleting pro každou z nich před provedením odstranění.

    `IsDeleting` má hodnotu true.

2. <xref:Microsoft.VisualStudio.Modeling.ModelElement.OnDeleted%2A> je volána, když se odstranil elementu. Zůstane v haldě modulu CLR, aby vrácení zpět lze provést, pokud je to nutné, ale je byl odpojen od jiných prvků a odebrána z `store.ElementDirectory`. U relací role stále odkazují na staré aktérů role.`IsDeleted` má hodnotu true.

3. Když uživatel vyvolá zpět po vytvoření elementu a starší odstranění se opakuje v znovu, se nazývají OnDeleting a OnDeleted. Použití `this.Store.InUndoRedoOrRollback` , aby aktualizace úložiště prvky v těchto případech. Další informace najdete v tématu [postupy: používání transakcí k aktualizaci modelu](../modeling/how-to-use-transactions-to-update-the-model.md).

   Následující kód například odstraní při odstranění jeho posledního podřízeného skladby alba:

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

 Často je užitečné aktivační událost před odstraněním vztah než role element vzhledem k tomu, že tento postup funguje, i když se odstraní prvek, a při odstranění samotného relace. Ale pro vztah odkazu můžete chtít rozšířit odstranění související prvek je odstraněn, ale ne v případě, že se odstraní samotnou relaci. Tento příklad odstraní alba při odstranění jeho poslední přispívající interpreta, ale neodpovídá relace budou odstraněny:

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

 Při provádění <xref:Microsoft.VisualStudio.Modeling.ModelElement.Delete%2A> na element, bude volána OnDeleting a OnDeleted. Tyto metody jsou vždy provádí vložení – to znamená, bezprostředně před a po jeho skutečné odstranění. Pokud váš kód odstraní nejmíň dva elementy, OnDeleting a OnDeleted bude volána v alternace všem z nich pak.

## <a name="rules"></a> Odstranění pravidla a události
 Jako alternativu k obslužné rutiny elementy OnDelete můžete definovat pravidla odstranění a odstranění události.

1.  **Odstraňuje se** a **odstranit** pravidla se spouštějí jenom v rámci transakce a ne v k vrácení zpět nebo opakování akce. Můžete nastavit, je zařadí do fronty ke spuštění na konci transakce, ve kterém se provádí odstranění. Odstranění pravidla jsou vždy spuštěn dříve, než všechny odstraněné pravidla, které jsou ve frontě.

     Použití pravidla šířící změny, které mají vliv pouze na prvky v úložišti, včetně vztahů, elementy diagramu a jejich vlastnosti. Obvykle odstranění pravidlo se používá k odstranění rozšíření a odstranit pravidlo se používá k vytvoření nahrazení elementů a vztahů.

     Další informace najdete v tématu [pravidla šíření změn v rámci the Model](../modeling/rules-propagate-changes-within-the-model.md).

2.  **Odstranit** úložiště událostí je vyvolána na konci transakce a je volána po provedení vrácení zpět nebo opakování akce. Proto ji můžete použít k rozšíření odstranění objektů mimo úložiště, například soubory, položky databáze nebo jiných objektů v sadě Visual Studio.

     Další informace najdete v tématu [obslužné rutiny rozšíření změny mimo the Model událostí](../modeling/event-handlers-propagate-changes-outside-the-model.md).

    > [!WARNING]
    >  Po odstranění prvku mají přístup k příslušné hodnoty vlastnosti domény, ale nedá se Navigovat vztah odkazy. Pokud jste nastavili pro odstraněnou událost na relaci, dostanete také dva prvky, které byly jeho aktérů role. Proto pokud chcete reagovat na odstranění prvku modelu, ale chtějí přístup k elementu, do které byl propojen, nastavení odstranění události v relaci místo prvku modelu doménové třídy.

### <a name="example-deletion-rules"></a>Příklad pravidla odstranění

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

### <a name="example-deleted-event"></a>Příklad pro odstraněnou událost

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

## <a name="unmerge"></a> Zrušit sloučení
 Operace, která připojí podřízený element svého nadřazeného objektu je volána *sloučení*. Nastane při nového elementu nebo skupiny prvků je vytvořena z panelu nástrojů nebo přesunut z jiné části modelu nebo zkopírovaných z schránky. A také vytváří vztah obsažení mezi nadřazenou a její nové podřízené operaci sloučení také nastavit další relace, vytvořte pomocné prvky a nastavit hodnoty vlastností v prvcích. Operace sloučení je zapouzdřena v elementu sloučení – direktiva (EMD).

 EMD zapouzdřuje také doplňující *oddělit* nebo `MergeDisconnect` operace. Pokud máte cluster prvků, který byl vytvořen pomocí sloučení, doporučuje se použít přidruženého oddělit odebrat element z něj, pokud chcete nechat zbývající prvky v konzistentním stavu. Operace oddělit bude obvykle pomocí technik popsaných v předchozích částech.

 Další informace najdete v tématu [přizpůsobení vytvoření a přesunutí elementu](../modeling/customizing-element-creation-and-movement.md).

## <a name="see-also"></a>Viz také

- [Přizpůsobení chování kopírování](../modeling/customizing-copy-behavior.md)
- [Přizpůsobení vytvoření a přesunutí elementu](../modeling/customizing-element-creation-and-movement.md)
- [Zápis kódu pro úpravu jazyka specifického pro doménu](../modeling/writing-code-to-customise-a-domain-specific-language.md)