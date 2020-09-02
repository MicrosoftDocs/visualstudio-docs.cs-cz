---
title: Správa modelů a diagramů v rámci správy verzí | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- models, version control
ms.assetid: ca6443e3-6d11-4da8-aae7-ca7dcc410076
caps.latest.revision: 32
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: b30b13610cc59b8a0225e52abf47f9a4f2cc97d1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72657581"
---
# <a name="manage-models-and-diagrams-under-version-control"></a>Správa modelů a diagramů pomocí správy verzí
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Spravujte různé verze projektů a diagramů modelování, včetně map kódu (soubory. dgml), pomocí možnosti [použít Team Foundation – správa verzí nebo Git](https://msdn.microsoft.com/library/33267cee-fe5f-4aa3-b2cd-6d22ceace314); buď s místními Team Foundation Server nebo v cloudu s Visual Studio Team Services.

 Chcete-li zjistit, které verze aplikace Visual Studio tuto funkci podporují, přečtěte si téma [podpora verzí pro nástroje pro architekturu a modelování](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

> [!IMPORTANT]
> Pokud pracuje několik uživatelů na stejném projektu modelování, buďte opatrní. Zjistěte, jak můžete [organizovat modely ve středních nebo rozsáhlých projektech](../modeling/structure-your-modeling-solution.md).

## <a name="files-in-a-modeling-project"></a><a name="ModelingProjects"></a> Soubory v projektu modelování
 Více než jeden uživatel může pracovat na projektu modelování současně, pokud pracuje na různých souborech.

 Chcete-li předejít nebo vyřešit konflikty mezi změnami provedenými různými uživateli, je důležité pochopit, jak je model uložen v souborech.

- Každý balíček je uložený v samostatném souboru **. UML** , který je uložený ve složce projektu **ModelDefinition** . Model má také soubor **. UML** . Pokud je některý z těchto souborů odstraněný nebo poškozený, odpovídající balíček nebo model se ztratí.

- Každý diagram je uložen ve dvou souborech. Například diagram třídy má:

  - **Schéma. classdiagram** – Pokud je tento soubor odstraněn nebo je poškozen, diagram bude ztracen, ale třídy a asociace, které byly zobrazeny, budou stále v modelu a lze je zobrazit v PRŮZKUMNÍKU modelů UML.

  - **Schéma. classdiagram. Layout** – Pokud je tento soubor odstraněn, budou se obrazce stále zobrazovat v diagramu, ale ztratí jejich velikosti a pozice. Každý soubor rozložení je dceřiným souborem diagramu. Pokud se chcete podívat, klikněte na [+] vedle souboru diagramu v Průzkumník řešení.

> [!NOTE]
> Je důležité zachovat konzistenci mezi soubory. Například pokud použijete správu zdrojového kódu k vrácení změn v souboru. UML, měli byste vrátit zpět odpovídající změny v souborech. * diagram a. Layout současně. Prvky reprezentované v. \* soubor diagramu bude ztracen, pokud nejsou také zastoupeny v souboru. Uml.

## <a name="working-on-shared-modeling-projects"></a><a name="Shared"></a> Práce na sdílených projektech modelování
 Minimalizace konfliktů mezi souběžnou prací na různých částech projektu:

- Rozdělte svůj projekt modelování do balíčků představujících různé oblasti práce. Přesuňte celý model do balíčků namísto jeho pochodu do kořenového modelu. Další informace najdete v tématu [Definování balíčků a oborů názvů](../modeling/define-packages-and-namespaces.md).

- Různí uživatelé by neměli pracovat současně na stejném balíčku nebo diagramu.

- Pokud používáte profily, ujistěte se, že všichni uživatelé nainstalovali stejné profily. Viz [Přizpůsobení modelu pomocí profilů a stereotypů](../modeling/customize-your-model-with-profiles-and-stereotypes.md).

- Abyste se ujistili, že měníte jenom balíček, na kterém pracujete:

  - Nastavte vlastnost **LinkedPackage** třídy UML, komponenty nebo diagramu případu použití.

  - V Průzkumníku modelů UML přetáhněte aktivitu nebo interakci do balíčku hned po jeho vytvoření. Tento prvek se zobrazí v Průzkumníku modelů UML při vytvoření prvního uzlu v aktivitě nebo sekvenčním diagramu.

- Abychom vám pomohli sledovat balíčky, přejmenujte soubory balíčku tak, aby odrážely skutečné názvy balíčků.

- V nástroji [!INCLUDE[esprscc](../includes/esprscc-md.md)] vždy provádějte operace **vrátit se změnami** a **získat nejnovější verze** v dokončeném projektu modelování, nikdy u jednotlivých souborů.

- Vždy proveďte operaci **získat** hned předtím, než se vrátíte do projektu modelování.

- Před provedením operace **Get** vždy zavřete všechny diagramy.

    > [!NOTE]
    > Pokud je soubor otevřený při provedení operace **Get**a výsledkem operace jsou místní změny, zobrazí se výzva k opětovnému načtení souboru. V takovém případě klikněte na tlačítko **ne**a pak znovu načtěte celý projekt. V **Průzkumník řešení**klikněte pravým tlačítkem myši na uzel projekt modelování, klikněte na položku **Uvolnit projekt**a poté klikněte na možnost **znovu načíst projekt**.

### <a name="changes-requiring-exclusive-access-to-the-model"></a><a name="Exclusive"></a> Změny vyžadující výhradní přístup k modelu
 Než provedete následující typy změn, ujistěte se, že máte zámek rezervace u celého projektu.

- Přejmenování nebo odstranění prvků, které jsou odkazovány z jiných balíčků.

- Změna vlastností relací, které překračují hranice balíčku.

- Další informace o zámkech najdete v tématu [rezervace a úpravy souborů](https://msdn.microsoft.com/library/eb404d63-c448-4994-9416-3e6d50ec554a).

##### <a name="to-move-a-diagram-file-in-or-out-of-a-project-folder"></a>Přesunutí souboru diagramu do nebo ze složky projektu

1. Spusťte **příkazový řádek pro vývojáře pro Visual Studio**.

2. Pomocí **TF přejmenovat** můžete přesunout soubor diagramu a jeho soubor **. Layout** :

     `tf rename sourcePath targetPath`

3. V Průzkumník řešení klikněte pravým tlačítkem na soubor a pak klikněte na **vyloučit z projektu**.

4. Přidejte soubor do cílové složky.

     V Průzkumník řešení klikněte pravým tlačítkem myši na cílovou složku nebo na projekt, přejděte na **Přidat**a pak klikněte na **existující položka**. V dialogovém okně vyberte soubor diagramu a pak klikněte na tlačítko **Přidat**. Soubor rozložení se přidá automaticky.

    > [!NOTE]
    > Soubor nelze přesunout do jiného projektu.

## <a name="merging-changes-in-model-files-and-diagrams"></a><a name="Merging"></a> Sloučení změn v souborech modelů a diagramech
 Když na modelu současně pracoval více než jeden uživatel, [!INCLUDE[esprscc](../includes/esprscc-md.md)] zobrazí se výzva ke sloučení změn v souborech modelu. Při práci na samostatných projektech, jak je popsáno v předchozích částech, se vyhnete většině sloučení. Zbývající konflikty je obvykle možné bezpečně sloučit automaticky. Následující typy změn by neměly způsobovat žádné potíže:

- Typy životností. Když přidáte životnost do interakce (sekvenční diagram), jeho typ je uložen v kořenovém modelu, pokud jste nevytvořili životnost z existujícího typu.

- Nové aktivity a interakce se zpočátku ukládají do kořenového modelu.

- Přidávání elementů a vztahů.

- Přejmenování nebo odstranění prvků, které jsou odkazovány pouze v rámci svého vlastního balíčku.

## <a name="see-also"></a>Viz také
 [Analýza a modelování](../modeling/analyze-and-model-your-architecture.md) [modelů sdílení a exportování diagramů](../modeling/share-models-and-exporting-diagrams.md)
