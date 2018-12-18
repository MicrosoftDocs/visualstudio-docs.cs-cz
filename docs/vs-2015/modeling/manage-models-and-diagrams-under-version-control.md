---
title: Správa modelů a diagramů pomocí správy verzí | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- models, version control
ms.assetid: ca6443e3-6d11-4da8-aae7-ca7dcc410076
caps.latest.revision: 32
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 20cb2e89a85f00782a172245dcdd8f47025ddd12
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51738049"
---
# <a name="manage-models-and-diagrams-under-version-control"></a>Správa modelů a diagramů pomocí správy verzí
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Spravovat různé verze projekty modelování a diagramy, včetně mapy kódu (soubory .dgml), pomocí [pomocí správy verzí Team Foundation nebo Git](http://msdn.microsoft.com/library/33267cee-fe5f-4aa3-b2cd-6d22ceace314); buď místní Team Foundation Server nebo v cloudu s Vizuálem Studio Team Services.  
  
 Tuto funkci podporovat kterou verzí sady Visual Studio najdete v tématu [podporované verze pro nástroje architektury a modelování](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  
  
> [!IMPORTANT]
>  Buďte opatrní při práci více uživatelů na stejném projektu modelování. Zjistěte, jak můžete [uspořádat modely ve střední a velké projekty](../modeling/structure-your-modeling-solution.md).  
  
##  <a name="ModelingProjects"></a> Soubory v projektu modelování  
 Více uživatelů může pracovat na projektu modelování ve stejnou dobu, pracují na různých souborech.  
  
 K zamezení nebo řešení konfliktů mezi změn provedenými různými uživateli, je důležité pochopit, jak je model uložen v souborech.  
  
-   Každý balíček je uložen ve zvláštním **.uml** soubor, který je uložen v **ModelDefinition** složky projektu. Model obsahuje také **.uml** souboru. Pokud některý z těchto souborů je odstraněn nebo poškozen, odpovídající balíček nebo model budou ztraceny.  
  
-   Každý diagram je uložen ve dvou souborech. Diagram třídy má například:  
  
    -   **DiagramName.classdiagram** – Pokud je tento soubor odstraněn nebo poškozen, diagram budou ztraceny, ale třídy a přidružení, která ukazoval bude i nadále v modelu a lze je zobrazit v Průzkumníku modelů UML.  
  
    -   **DiagramName.classdiagram.layout** -li tento soubor odstraněn, tvary se nadále zobrazí v diagramu, ale dojde ke ztrátě jejich velikostí a umístění. Každý soubor rozložení je podřízený souboru diagramu. Zobrazíte ho kliknutím na [+] vedle souboru diagramu v Průzkumníku řešení.  
  
> [!NOTE]
>  Je důležité zajistit konzistenci těchto souborů. Například pokud používáte správy zdrojového kódu vrátit zpět provedené změny v souboru s příponou UML, měli byste vrátit zpět odpovídající změny. * diagram a .layout soubory ve stejnou dobu. Elementy zastoupené v. \*soubor diagramu budou ztraceny, pokud nejsou také reprezentovány v souboru .uml.  
  
##  <a name="Shared"></a> Práce na sdílených projektech modelování  
 Chcete-li minimalizovat konflikty mezi souběžnou prací na různých částech projektu:  
  
-   Modelování projektu rozdělte do balíčků zastupujících různé oblasti činnosti. Přesuňte celý model do balíčků, namísto jeho ponechání v kořenovém modelu. Další informace najdete v tématu [definování balíčků a oborů názvů](../modeling/define-packages-and-namespaces.md).  
  
-   Různí uživatelé by neměli pracovat na stejném balíčku nebo diagramu současně.  
  
-   Pokud používáte profily, ujistěte se, že všichni uživatelé nainstalovali stejné profily. Zobrazit [přizpůsobení modelu pomocí profilů a stereotypů](../modeling/customize-your-model-with-profiles-and-stereotypes.md).  
  
-   Abyste zajistili, že změníte pouze balíček, na které pracujete:  
  
    -   Nastavte **LinkedPackage** vlastnost třídy UML, komponenty nebo diagramu případu použití.  
  
    -   V Průzkumníku modelů UML přetáhněte aktivitu nebo interakci do balíčku ihned po jeho vytvoření. Tento prvek se zobrazí v Průzkumníku modelů UML při vytvoření prvního uzlu v činnosti nebo sekvenčním diagramu.  
  
-   Abyste mohli udržovat přehled o balíčky, přejmenujte soubory balíčku tak, aby odrážely skutečné názvy balíčku.  
  
-   V [!INCLUDE[esprscc](../includes/esprscc-md.md)], vždy provádět **vrátit se změnami** a **získat nejnovější verzi** operace na dokončeném projektu modelování, nikdy ne na jednotlivé soubory.  
  
-   Vždy provádět **získat** operace bezprostředně před vrácením projektu modelování.  
  
-   Před provedením vždy zavřít všechny diagramy **získat** operace.  
  
    > [!NOTE]
    >  Pokud je soubor otevřen při provedení **získat**, a operace vyústí v místní změny, pak budete vyzváni k opětovnému načtení souboru. V tomto případě klikněte na tlačítko **ne**a pak znovu načtěte celý projekt. V **Průzkumníka řešení**, modelování klikněte pravým tlačítkem na uzel projektu, klikněte na tlačítko **uvolnit projekt**a potom klikněte na tlačítko **znovu načíst projekt**.  
  
###  <a name="Exclusive"></a> Změny vyžadující výhradní přístup k modelu  
 Před provedením následující typy změn, ujistěte se, že máte zámek rezervování na celém projektu.  
  
-   Přejmenování nebo odstranění prvků, které jsou odkazovány z jiných balíčků.  
  
-   Změna vlastností vztahů, které překračují hranice balíčku.  
  
-   Další informace o zámcích pro rezervaci, naleznete v tématu [zkontrolujte out a úpravy souborů](http://msdn.microsoft.com/library/eb404d63-c448-4994-9416-3e6d50ec554a).  
  
##### <a name="to-move-a-diagram-file-in-or-out-of-a-project-folder"></a>Chcete-li přesunout soubor diagramu do nebo ze složky projektu  
  
1.  Spustit **Developer Command prompt pro Visual Studio**.  
  
2.  Použití **tf přejmenovat** přesunout soubor diagramu a jeho **.layout** souboru:  
  
     `tf rename sourcePath targetPath`  
  
3.  V Průzkumníku řešení klikněte pravým tlačítkem myši na soubor a pak klikněte na tlačítko **vyjmout z projektu**.  
  
4.  Přidejte soubor do cílové složky.  
  
     V Průzkumníku řešení klikněte pravým tlačítkem na cílovou složku nebo projekt, přejděte na **přidat**a potom klikněte na tlačítko **existující položku**. V dialogovém okně vyberte soubor diagramu a potom klikněte na tlačítko **přidat**. Soubor rozložení se přidají automaticky.  
  
    > [!NOTE]
    >  Soubor nelze přesunout do jiného projektu.  
  
##  <a name="Merging"></a> Sloučení změn v souborech a diagramech modelů  
 Po více než jeden uživatel má na modelu pracovat současně, [!INCLUDE[esprscc](../includes/esprscc-md.md)] vás vyzve ke sloučení změn v souborech modelu. Práce na samostatných projektech jak je popsáno v předchozích částech zabrání většině sloučení. Obvykle další konflikty lze bezpečně sloučit automaticky. Následující typy změn by neměly způsobit žádné problémy:  
  
-   Typy životností. Když přidáte do interakce (sekvenční diagram) životnost, jeho typ je uložen do kořenového modelu, pokud jste nevytvořili životnost z existujícího typu.  
  
-   Nové aktivity a interakce musí být nejprve uloženy v kořenovém modelu.  
  
-   Přidání prvků a vztahů.  
  
-   Přejmenování nebo odstranění prvků, které jsou uvedeny pouze v rámci vlastního balíčku.  
  
## <a name="see-also"></a>Viz také  
 [Analýza a modelování vaší architektury](../modeling/analyze-and-model-your-architecture.md)   
 [Sdílení modelů a export diagramů](../modeling/share-models-and-exporting-diagrams.md)



