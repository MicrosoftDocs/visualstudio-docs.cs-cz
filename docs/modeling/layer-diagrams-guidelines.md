---
title: 'Diagramy závislostí: Pokyny'
description: Naučte se popsat architekturu vaší aplikace na vysoké úrovni tím, že vytvoříte diagramy závislosti v aplikaci Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 09/28/2018
ms.topic: conceptual
helpviewer_keywords:
- architecture, dependency diagrams
- dependency diagrams
- diagrams - modeling, layer
- constraints, architectural
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: f46e2b774cd4da2ef9cdb9ddef7efd19f731ade7
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/19/2021
ms.locfileid: "112391020"
---
# <a name="dependency-diagrams-guidelines"></a>Diagramy závislostí: pokyny

Popište architekturu vaší aplikace na vysoké úrovni tím, že vytvoříte *diagramy závislosti* v aplikaci Visual Studio. Ujistěte se, že váš kód zůstává v souladu s tímto návrhem ověřováním kódu pomocí diagramu závislostí. Do procesu sestavení můžete také zahrnout ověřování vrstvy. Podívejte [se na video pro kanál 9: návrh a ověření architektury pomocí diagramů závislostí](https://channel9.msdn.com/Series/Visual-Studio-2012-Premium-and-Ultimate-Overview/Visual-Studio-Ultimate-2012-Using-layer-diagrams-to-design-and-validate-your-architecture).

Pokud chcete zjistit, které edice sady Visual Studio podporují tuto funkci, přečtěte si téma [Podpora edice pro nástroje pro architekturu a modelování](../modeling/analyze-and-model-your-architecture.md#VersionSupport).

> [!NOTE]
> Diagramy závislostí pro projekty .NET Core jsou podporovány počínaje verzí Visual Studio 2019 verze 16,2.

## <a name="what-is-a-dependency-diagram"></a>Co je Diagram závislostí?

Podobně jako v případě klasického diagramu architektury identifikuje diagram závislosti hlavní součásti nebo funkční jednotky návrhu a jejich vzájemných závislostí. Každý uzel v diagramu, označovaný jako *vrstva*, představuje logickou skupinu oborů názvů, projektů nebo jiných artefaktů. Můžete nakreslit závislosti, které by měly existovat v návrhu. Na rozdíl od tradičního diagramu architektury můžete ověřit, zda skutečné závislosti ve zdrojovém kódu odpovídají plánovaným závislostem, které jste určili. Při ověřování části pravidelného sestavení na [!INCLUDE[esprtfs](../code-quality/includes/esprtfs_md.md)] portálu můžete zajistit, aby kód programu pokračoval v dodržení architektury systému v důsledku budoucích změn. Viz téma [diagramy závislostí: Reference](../modeling/layer-diagrams-reference.md).

## <a name="how-to-design-or-update-your-app-with-dependency-diagrams"></a>Návrh nebo aktualizace aplikace pomocí diagramů závislostí

Následující kroky poskytují přehled o tom, jak používat diagramy závislosti v rámci procesu vývoje. Pozdější části tohoto tématu popisují další podrobnosti o jednotlivých krocích. Pokud vyvíjíte nový návrh, vynechejte postup, který odkazuje na existující kód.

> [!NOTE]
> Tyto kroky se zobrazí v přibližném pořadí. Pravděpodobně budete chtít překrývat úkoly, změnit jejich pořadí tak, aby vyhovovaly vaší vlastní situaci, a pak je znovu navštívit na začátku každé iterace v projektu.

1. [Vytvoření diagramu závislostí](#Create) pro celou aplikaci nebo pro vrstvu v ní.

2. [Definujte vrstvy, které reprezentují hlavní funkční oblasti nebo komponenty](#CreateLayers) vaší aplikace. Pojmenujte tyto vrstvy podle jejich funkce, například "prezentace" nebo "služby". Máte-li řešení sady Visual Studio, můžete přidružit jednotlivé vrstvy ke kolekci *artefaktů*, jako jsou například projekty, obory názvů, soubory a tak dále.

3. [Zjistí existující závislosti](#Generate) mezi vrstvami.

4. [Upravte vrstvy a závislosti](#EditArchitecture) tak, aby se zobrazil aktualizovaný návrh, který chcete, aby kód odrážel.

5. [Navrhněte nové oblasti aplikace](#NewAreas) vytvořením vrstev, které představují hlavní stavební bloky nebo komponenty, a definování závislostí, které ukazují, jak jednotlivé vrstvy používají ostatní.

6. [Upravte rozložení a vzhled diagramu](#EditLayout) , abyste ho mohli diskutovat s kolegy.

7. [Ověřte kód v diagramu závislostí](#Validate) a zvýrazněte konflikty mezi kódem a architekturou, kterou požadujete.

8. [Aktualizujte kód tak, aby odpovídal vaší nové architektuře](#UpdateCode). Iterativní vývoj a refaktoring kódu, dokud ověření neukáže žádné konflikty.

9. [Zahrňte ověřování vrstvy do procesu sestavení](#BuildValidation) , aby se zajistilo, že kód bude nadále vyhovovat vašemu návrhu.

## <a name="create-a-dependency-diagram"></a><a name="Create"></a> Vytvoření diagramu závislostí

Diagram závislostí musí být vytvořen v rámci projektu modelování. Nový diagram závislosti můžete přidat do existujícího projektu modelování, vytvořit nový projekt modelování pro diagram závislosti nebo zkopírovat existující diagram závislostí do stejného projektu modelování.

> [!IMPORTANT]
> Nepřidávat, přetahovat ani kopírovat existující diagram závislostí z projektu modelování do jiného projektu modelování nebo do jiného umístění v řešení. Diagram závislosti, který je zkopírován tímto způsobem, bude mít stejné odkazy jako původní diagram, i když diagram upravíte. To zabrání správnému fungování ověřování vrstvy a může způsobit další problémy, například chybějící prvky nebo jiné chyby při pokusu o otevření diagramu.

Viz [vytváření diagramů závislostí z kódu](../modeling/create-layer-diagrams-from-your-code.md).

## <a name="define-layers-to-represent-functional-areas-or-components"></a><a name="CreateLayers"></a> Definování vrstev pro reprezentaci funkčních oblastí nebo komponent

Vrstvy reprezentují logické skupiny *artefaktů*, jako jsou projekty, soubory kódu, obory názvů, třídy a metody. Můžete vytvořit vrstvy z artefaktů z projektů Visual C# a Visual Basic nebo můžete k vrstvě připojit specifikace nebo plány propojením dokumentů, jako jsou například soubory aplikace Word nebo prezentace aplikace PowerPoint. Každá vrstva se zobrazí jako obdélník v diagramu a zobrazuje počet artefaktů, které jsou s ním spojeny. Vrstva může obsahovat vnořené vrstvy, které popisují konkrétnější úlohy.

V rámci obecných pokynů, názvy vrstev podle jejich funkce, například "prezentace" nebo "služby". Pokud jsou artefakty úzce závislé, umístěte je do stejné vrstvy. Pokud se artefakty dají aktualizovat samostatně nebo použít v samostatných aplikacích, umístěte je do různých vrstev. Další informace o vzorech vrstvení najdete na webu vzory & postupy na adrese [http://go.microsoft.com/fwlink/?LinkId=145794](https://archive.codeplex.com/?p=apparch) .

> [!TIP]
> Existují určité typy artefaktů, které můžete propojit s vrstvami, ale které nepodporují ověřování proti diagramu závislostí. Chcete-li zjistit, zda artefakt podporuje ověřování, otevřete **Průzkumníka vrstev** a prověřte vlastnost **podporuje ověření** odkazu artefaktu. Viz [zjišťování existujících závislostí mezi vrstvami](#Generate).

Při aktualizaci neznámé aplikace můžete také vytvořit mapy kódu. Tyto diagramy vám mohou při zkoumání kódu pomáhat při vyhledávání vzorů a závislostí. Pomocí Průzkumník řešení můžete prozkoumat obory názvů a třídy, které často odpovídají existujícím vrstvám. Přiřaďte tyto artefakty kódu do vrstev jejich přetažením z Průzkumník řešení do diagramů závislostí. Pak můžete použít diagramy závislosti, které vám pomůžou aktualizovat kód a zachovat konzistenci s Vaším návrhem.

Přečtěte si:

- [Vytváření diagramů závislostí z kódu](../modeling/create-layer-diagrams-from-your-code.md)

- [Použití map kódu k ladění aplikací](../modeling/use-code-maps-to-debug-your-applications.md)

- [Mapování závislostí napříč vaším řešením](../modeling/map-dependencies-across-your-solutions.md)

## <a name="discover-existing-dependencies-between-layers"></a><a name="Generate"></a> Zjišťovat existující závislosti mezi vrstvami

Závislost existuje všude, kde artefakt, který je spojen s jednou vrstvou, odkazuje na artefakt, který je přidružen k jiné vrstvě. Třída v jedné vrstvě například deklaruje proměnnou, která má třídu v jiné vrstvě. Stávající závislosti můžete zjistit zpětnou metodologií.

> [!NOTE]
> Pro určité druhy artefaktů nelze provádět zpětnou analýzu žádných závislostí. Zpětnou analýzou například nebudou získány žádné závislosti z vrstvy nebo do ní, když je propojena s textovým souborem. Chcete-li zjistit, které artefakty mají závislosti, které je možné zpětně analyzovat, klikněte pravým tlačítkem myši na jednu nebo více vrstev a potom klikněte na možnost **Zobrazit odkazy**. V **Průzkumníku vrstev** Projděte sloupec **Podpora ověřování** . Pro artefakty, pro které tento sloupec zobrazuje **hodnotu false**, nebude možné provádět zpětnou analýzu závislostí.

### <a name="to-reverse-engineer-existing-dependencies-between-layers"></a>Zpětná analýza existujících závislostí mezi vrstvami

Vyberte jednu vrstvu nebo více vrstev, klikněte pravým tlačítkem na vybranou vrstvu a pak klikněte na **vygenerovat závislosti**.

Obvykle se zobrazí nějaké závislosti, které by neměly existovat. Tyto závislosti lze upravit, aby odpovídaly zamýšlenému návrhu.

## <a name="edit-layers-and-dependencies-to-show-the-intended-design"></a><a name="EditArchitecture"></a> Úprava vrstev a závislostí pro zobrazení zamýšleného návrhu

Chcete-li popsat změny, které plánujete udělat v systému nebo zamýšlené architektuře, použijte následující postup pro úpravu diagramu závislostí. Můžete také zvážit provedení některých změn refaktoringu pro zlepšení struktury kódu před jeho rozšířením. Viz [vylepšení struktury kódu](#Improving).

|**Do**|**Proveďte tyto kroky**|
|-|-|
|Odstranit závislost, která neexistuje|Klikněte na závislost a potom stiskněte **Delete**.|
|Změna nebo omezení směru závislosti|Nastavte vlastnost **Direction** .|
|Vytvoření nových závislostí|Použijte nástroje **závislosti** a **obousměrné závislosti** .<br /><br /> Chcete-li nakreslit více závislostí, klikněte na nástroj dvakrát. Po dokončení klikněte na nástroj **ukazatel** nebo stiskněte klávesu **ESC** .|
|Zadání toho, aby artefakty spojené s vrstvou nemohly záviset na zadaných oborech názvů|Zadejte obory názvů ve vlastnosti **zakázané závislosti oboru názvů** vrstvy. K oddělení oborů názvů použijte středník (**;**).|
|Zadání toho, aby artefakty spojené s vrstvou nesměly patřit zadanému oboru názvů|Zadejte obory názvů do vlastnosti **zakázané obory názvů** vrstvy. K oddělení oborů názvů použijte středník (**;**).|
|Zadání toho, aby artefakty spojené s vrstvou musely patřit jednomu ze zadaných oborů názvů|Zadejte obor názvů do vlastnosti **požadované obory názvů** vrstvy. K oddělení oborů názvů použijte středník (**;**).|

### <a name="improving-the-structure-of-the-code"></a><a name="Improving"></a> Zlepšení struktury kódu

Změny refaktoringu jsou vylepšení, která neovlivňují chování aplikace, ale usnadňují změnu a rozšiřování kódu v budoucnu. Dobře strukturovaný kód má návrh, který lze snadno abstrahovat do diagramu závislostí.

Pokud například vytvoříte vrstvu pro každý obor názvů v kódu a pak reverzní analýzu závislostí, měla by mezi vrstvami být minimální sada jednosměnných závislostí. Pokud vytvoříte podrobnější diagram pomocí tříd nebo metod jako vrstev, měl by mít výsledek také stejné charakteristiky.

Pokud tomu tak není, bude změna kódu v průběhu jeho životnosti obtížnější a bude méně vhodná pro ověřování pomocí diagramů závislostí.

## <a name="design-new-areas-of-your-application"></a><a name="NewAreas"></a> Návrh nových oblastí aplikace

Když začnete s vývojem nového projektu nebo nové oblasti v novém projektu, můžete nakreslit vrstvy a závislosti, které vám pomůžou identifikovat hlavní komponenty, než začnete vyvíjet kód.

- **Pokud je to možné, můžete** v diagramech závislostí zobrazit identifikovatelné vzory architektury. Například diagram závislostí, který popisuje desktopovou aplikaci, může zahrnovat vrstvy, jako je prezentace, logika domény a úložiště dat. Diagram závislostí, který pokrývá jednu funkci v rámci aplikace, může mít vrstvy, jako je model, zobrazení a kontroler. Další informace o těchto vzorech najdete v tématu [Patterns & Practices: Application Architecture](https://archive.codeplex.com/?p=apparch).

- **Vytvořte artefakt kódu pro každou vrstvu,** například obor názvů, třídu nebo komponentu. To usnadňuje sledování kódu a propojení artefaktů kódu s vrstvami. Jakmile každý artefakt vytvoříte, propoejte ho s příslušnou vrstvou.

- **Většinu tříd a dalších** artefaktů není třeba propojit s vrstvami, protože spadají do větších artefaktů, jako jsou obory názvů, které už máte propojené s vrstvami.

- **Vytvořte nový diagram pro novou funkci**. Obvykle bude k dispozici jeden nebo více diagramů závislostí popisujících celou aplikaci. Pokud v rámci aplikace navrhovat novou funkci, nepřidáte do stávajících diagramů ani je neměňte. Místo toho vytvořte vlastní diagram, který odráží nové části kódu. Vrstvy v novém diagramu můžou zahrnovat prezentační vrstvy, logiku domény a databázové vrstvy pro novou funkci.

     Při sestavování aplikace se váš kód ověří jak v celkovém diagramu, tak v podrobnějším diagramu funkcí.

## <a name="edit-the-layout-for-presentation-and-discussion"></a><a name="EditLayout"></a> Úprava rozložení pro prezentaci a diskuzi

Abyste mohli snadno identifikovat vrstvy a závislosti nebo je probrat se členy týmu, upravte vzhled a rozložení diagramu následujícími způsoby:

- Změňte velikosti, tvary a pozice vrstev.

- Změňte barvy vrstev a závislostí.

  - Vyberte jednu nebo více vrstev nebo závislostí, klikněte pravým tlačítkem a potom klikněte na **Vlastnosti**. V **okně Vlastnosti** upravte vlastnost **Color.**

## <a name="validate-the-code-against-the-diagram"></a><a name="Validate"></a> Ověření kódu v diagramu

Po úpravě diagramu ho můžete kdykoli ručně ověřit v kódu nebo automaticky pokaždé, když ho sestavíte.

Přečtěte si:

- [Ověřování kódu pomocí diagramů závislostí](../modeling/validate-code-with-layer-diagrams.md)

- [Zahrnutí ověření vrstvy do procesu sestavení](#BuildValidation)

## <a name="update-the-code-to-conform-to-the-new-architecture"></a><a name="UpdateCode"></a> Aktualizujte kód tak, aby odpovídal nové architektuře.

Chyby se obvykle zobrazí při prvním ověření kódu proti aktualizovanému diagramu závislostí. Tyto chyby mohou mít několik příčin:

- Artefakt je přiřazen nesprávné vrstvě. V tomto případě přesuňte artefakt.

- Artefakt, jako je například třída, používá jiné třídy způsobem, který je v konfliktu s architekturou. V tomto případě refaktorujte kód a odeberte závislost.

Chcete-li tyto chyby odstranit, aktualizujte kód, dokud se během ověřování neobjeví žádné chyby. Obvykle se jedná o iterativní proces. Další informace o těchto chybách najdete v tématu [Ověření kódu pomocí diagramů závislostí.](../modeling/validate-code-with-layer-diagrams.md)

> [!NOTE]
> Při vývoji nebo refaktoringu kódu můžete mít nové artefakty pro propojení s diagramem závislostí. To však nemusí být nutné, například pokud máte vrstvy, které představují existující obory názvů, a nový kód přidá do těchto oborů názvů pouze další materiály.

Během procesu vývoje můžete chtít potlačit některé vykázané konflikty během ověřování. Například můžete chtít potlačit chyby, které již řešíte nebo které nejsou relevantní k danému scénáři. Když chybu potlačíte, je vhodné protokolovat pracovní položku v Team Foundation. Pokud chcete tuto úlohu provést, podívejte [se na stránku Ověření kódu pomocí diagramů závislostí](../modeling/validate-code-with-layer-diagrams.md).

## <a name="include-layer-validation-in-the-build-process"></a><a name="BuildValidation"></a> Zahrnutí ověření vrstvy do procesu sestavení

Pokud chcete zajistit, aby budoucí změny v kódu odpovídaly diagramům závislostí, zahrpište ověřování vrstev do standardního procesu sestavení vašeho řešení. Kdykoli ostatní členové týmu sestaví řešení, všechny rozdíly mezi závislostmi v kódu a diagramem závislostí budou hlášeny jako chyby sestavení. Další informace o zahrnutí ověřování vrstev do procesu sestavení najdete v tématu Ověření [kódu pomocí diagramů závislostí.](../modeling/validate-code-with-layer-diagrams.md)

## <a name="see-also"></a>Viz také

- [Diagramy závislostí: Referenční dokumentace](../modeling/layer-diagrams-reference.md)
- [Vytváření diagramů závislostí z kódu](../modeling/create-layer-diagrams-from-your-code.md)
