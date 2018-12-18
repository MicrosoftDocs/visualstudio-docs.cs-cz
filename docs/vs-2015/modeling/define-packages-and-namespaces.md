---
title: Definování balíčků a oborů názvů | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- UML model, namespaces
- UML, namespaces
- UML, packages
- UML model, packages
ms.assetid: 79147068-02d5-4b70-933d-f647c1da3829
caps.latest.revision: 22
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: b9295b5af83270069df11e6460ee85dfe0fd9c73
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51741908"
---
# <a name="define-packages-and-namespaces"></a>Definování balíčků a oborů názvů
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

V sadě Visual Studio *balíčku* je kontejner pro definice elementů UML, jako jsou třídy, případy použití a komponenty. Balíček může obsahovat také další balíčky.  
  
 V Průzkumníku modelů UML jsou všechny definice uvnitř balíčku vnořené pod balíček. UML model je druh balíček a vytváří kořen stromu.  
  
 Tuto funkci podporovat kterou verzí sady Visual Studio najdete v tématu [podporované verze pro nástroje architektury a modelování](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  
  
## <a name="in-this-topic"></a>V tomto tématu  
 [Obory názvů](#Namespaces)  
  
 [Vytváření a zobrazení balíčků](#Packages)  
  
 [Vytvoření modelu elementů v rámci balíčky](#Elements)  
  
 [Přesouvání elementů do nebo z něj balíček](#Moving)  
  
 [Vkládání elementů do balíčku](#Pasting)  
  
 [Importovat relace mezi balíčky](#Import)  
  
 [Odkazy z jednoho Namespace](#References)  
  
 [Vlastnosti balíčků](#Properties)  
  
##  <a name="Namespaces"></a> Obory názvů  
 Balíčky jsou užitečné pro oddělení práce do různých oblastí. Každý balíček definuje obor názvů tak, aby názvy, které jsou definovány v různých balíčcích nejsou v konfliktu mezi sebou.  
  
 Vlastnost kvalifikovaný název každého prvku je úplný název balíčku, do které patří, a potom podle názvu vlastního elementu. Například, pokud váš balíček se nazývá `MyPackage`, třídu v rámci balíčku, budou mít úplný název jako `MyPackage::MyClass`. Protože každý prvek se nachází v modelu, každý kvalifikovaný název začíná názvem modelu.  
  
 Model také definuje obor názvů, tak, aby kvalifikovaný název člena každý prvek v modelu začíná název modelu.  
  
 Ostatní prvky modelu také definovat obory názvů. Například operace patří do oboru názvů určené své nadřízené třídy tak, aby její kvalifikovaný název je jako `MyModel ::MyPackage ::MyClass ::MyOperation`. Stejným způsobem patří akci pro obor názvů definovaný smyčkou její nadřazená aktivita.  
  
 Balíčky jsou kontejnery. Je-li přesunout nebo odstranit balíček, tříd, balíčky a další věci definované uvnitř ho také přesunutí nebo odstranění. Totéž platí další prvky, které definují obory názvů.  
  
##  <a name="Packages"></a> Vytváření a zobrazení balíčků  
 Balíček můžete vytvářet v diagramu tříd UML, nebo v Průzkumníku modelů UML.  
  
#### <a name="to-create-a-package-in-a-uml-class-diagram"></a>Chcete-li vytvořit balíček v diagramu tříd UML  
  
1.  Otevřete diagram tříd UML, nebo vytvořte novou.  
  
2.  Klikněte na tlačítko **balíčku** nástroj.  
  
3.  Klikněte kamkoli v diagramu. Zobrazí se nový balíček tvar.  
  
     Klikněte na tlačítko v existující balíček vnořit jeden balíček v jiném.  
  
4.  Zadejte nový název pro balíček.  
  
#### <a name="to-create-a-package-in-uml-model-explorer"></a>Chcete-li vytvořit balíček v Průzkumníku modelů UML  
  
1. Otevřít **Průzkumníku modelů UML**. Na **architektura** nabídky, přejděte k **Windows**a potom klikněte na tlačítko **Průzkumníku modelů UML**.  
  
2. Klikněte pravým tlačítkem na balíček nebo model, ke kterému chcete přidat nový balíček.  
  
   > [!NOTE]
   >  Je možné vnořovat balíček uvnitř jiného balíčku.  
  
3. Přejděte na **přidat** a potom klikněte na tlačítko **balíčku**.  
  
    V modelu se zobrazí nový balíček.  
  
4. Zadejte nový název pro balíček.  
  
   Když vytvoříte balíček v Průzkumníku modelů UML je můžete zobrazit v diagramu tříd UML. Balíček můžete zobrazit také na více než jednoho diagramu tříd UML.  
  
#### <a name="to-show-an-existing-package-on-a-uml-class-diagram"></a>Chcete-li zobrazit existující balíček v diagramu tříd UML  
  
-   Přetáhněte tento balíček z Průzkumníku modelů UML na diagram tříd.  
  
    > [!NOTE]
    >  Tím se vytvoří zobrazení balíčku na tomto diagramu. Nezobrazí se nutně všechny prvky, že balíček obsahuje. Ujistěte se, že se zobrazí veškerý obsah pro balíček, že ji zobrazte v Průzkumníku modelů UML.  
  
##  <a name="Elements"></a> Vytvoření modelu elementů v rámci balíčky  
 Existují čtyři způsoby, ve kterých můžete umístit prvky modelu uvnitř balíčku:  
  
- Přidáte nový prvek do balíčku v Průzkumníku modelů UML.  
  
- Přidáte třídami a ostatními typy balíčků v diagramu tříd UML.  
  
- Nastavte **LinkedPackage** vlastnictví diagramu tak, aby nové prvky vytvořené v diagramu jsou umístěné uvnitř balíčku, který zadáte. Do balíčku tímto způsobem lze propojit diagramů tříd, komponenta diagramy a diagramy případů použití.  
  
- Přesuňte elementy do nebo z něj balíček v Průzkumníku modelů UML.  
  
  Element v balíčku se zobrazí pod balíček v Průzkumníku modelů UML a jeho kvalifikovaný název začíná na úplný název balíčku. Pokud chcete zobrazit úplný název libovolný element, klikněte pravým tlačítkem na prvek a potom klikněte na **vlastnosti**. **Kvalifikovaný název** vlastnost se zobrazí v **vlastnosti** okna.  
  
#### <a name="to-create-an-element-in-a-package-in-uml-model-explorer"></a>Chcete-li vytvořit element v balíčku v Průzkumníku modelů UML  
  
1.  Otevřít **Průzkumníku modelů UML**. Na **zobrazení** nabídky, přejděte k **ostatní Windows**a potom klikněte na tlačítko **Průzkumníku modelů UML**.  
  
2.  Klikněte pravým tlačítkem na balíček nebo model, ke kterému chcete přidat nový prvek.  
  
3.  Přejděte na **přidat**a potom klikněte na typ prvku, který chcete přidat.  
  
     Nový prvek se zobrazí pod balíček.  
  
4.  Zadejte název pro nový prvek.  
  
    > [!NOTE]
    >  Nový prvek se nezobrazí na jakýkoliv diagram. Vytvoření zobrazení nového elementu, ji můžete přetáhnout z Průzkumníku modelů UML do diagramu. Diagram musí být typ, který se zobrazí tento typ elementu.  
  
#### <a name="to-create-an-element-in-a-package-on-a-uml-class-diagram"></a>Chcete-li vytvořit element v balíčku v diagramu tříd UML  
  
1.  Otevřete diagram třídy, na kterém se zobrazí balíčku.  
  
    -   Pokud jste to ještě neudělali, vytvořte nový balíček.  
  
    -   Chcete-li existující balíček se zobrazí v diagramu tříd, můžete přetáhnout balíček z **Průzkumníku modelů UML** do diagramu tříd.  
  
2.  Klikněte na nástroj pro třídy, rozhraní nebo výčet nebo balíčku.  
  
3.  Klikněte na balíček, ve kterém chcete vložit nový prvek.  
  
     Nový prvek se zobrazí uvnitř balíčku.  
  
#### <a name="to-create-all-the-elements-of-a-diagram-in-a-specified-package"></a>Chcete-li vytvořit všechny prvky diagramu v zadaném balíčku  
  
1.  Vytvoření balíčku, pokud jste to ještě neudělali.  
  
2.  Otevřete diagram komponent, diagram případu použití nebo diagram tříd UML.  
  
3.  Otevřete vlastnosti diagramu. Klikněte pravým tlačítkem na prázdnou část diagramu a potom klikněte na tlačítko **vlastnosti**.  
  
4.  V **odkazovaný balíček** vlastnosti, vyberte balíček, který má obsahovat obsah do diagramu.  
  
5.  Vytvoření nových prvků v diagramu. Tyto budou umístěny do balíčku.  
  
    -   **Kvalifikovaný název** jednotlivých prvků bude začínat úplný název balíčku.  
  
    -   V **Průzkumníku modelů UML**, se zobrazí každý prvek v rámci balíčku.  
  
##  <a name="Moving"></a> Přesouvání elementů do proměnné a z balíčků  
 Jeden nebo více prvků lze přesunout, nebo z balíčku.  
  
 Pokud přesunete balíčku, celý její obsah se přesune s ním.  
  
#### <a name="to-move-an-element-into-or-out-of-a-package"></a>Přesunout element do nebo z něj balíček  
  
-   V Průzkumníku modelů UML přetáhněte prvek do nebo z něj stromu, jejichž kořenový adresář je balíček.  
  
     Kvalifikovaný název elementu se změní na zobrazit jeho nové vlastnícího balíčku nebo modelu.  
  
     \- nebo –  
  
-   V diagramu tříd přetáhněte prvek do balíčku obrazce.  
  
     Kvalifikovaný název elementu se změní na zobrazit jeho nové vlastnícího balíčku.  
  
    > [!NOTE]
    >  Přetáhněte element z balíčku do prázdné části diagramu, jeho vlastnícího balíčku nezmění. Tímto způsobem můžete vytvořit diagram, který zobrazuje prvky z několika balíčky bez nutnosti zobrazit balíčky sami.  
  
##  <a name="Pasting"></a> Vkládání elementů do balíčku  
 Element můžete vložit do balíčku. Pokud skupina souvisejících prvků vložíte do balíčku, bude také vložit vztahy mezi nimi.  
  
#### <a name="to-paste-elements-into-a-package-on-a-uml-class-diagram"></a>Chcete-li vložit prvky do balíčku v diagramu tříd UML  
  
1.  V diagramu tříd UML vyberte všechny elementy, které chcete kopírovat. Klikněte pravým tlačítkem na jeden z nich a pak klikněte na tlačítko **kopírování**.  
  
2.  Klikněte pravým tlačítkem na balíček a pak klikněte na tlačítko **vložit**.  
  
    > [!NOTE]
    >  Balíček může být v různých diagramu.  
  
##  <a name="Import"></a> Importovat relace mezi balíčky  
 Můžete definovat vztah import mezi balíčky pomocí **importovat** nástroj.  
  
 Import znamená, že elementy definovaných v importované balíčku, které jsou prvky na konci šipku relace, jsou efektivně definovány také v importu balíčku. Elementy jehož viditelnosti je definován jako **balíčku** budou viditelné také v importu balíčku.  
  
 Vyhněte se vytváření smyčky ve vztazích importu.  
  
##  <a name="References"></a> Odkazy z jednoho Namespace  
 Pokud chcete odkazovat na prvek jeden balíček z jiného, musíte použít kvalifikovaný název daného elementu.  
  
 Předpokládejme například, že balíček `SalesCommon` definuje typ `CustomerAddress`. V dalším balíčku `RestaurantSales`, můžete definovat typ `MealOrder`, který má atribut typu adresy zákazníka. Máte dvě možnosti:  
  
-   Zadejte typ atributu pomocí plně kvalifikovaného názvu `SalesCommon::CustomerAddress`. Byste měli dělat pouze pokud mohou `CustomerAddress` má jeho **viditelnost** vlastnost nastavena na hodnotu **veřejné**.  
  
-   Vytvoří vztah Import z `RestaurantSales` balíček do `SalesCommon` balíčku. Můžete použít `CustomerAddress` bez použití jeho kvalifikovaný název.  
  
##  <a name="Properties"></a> Vlastnosti balíčků  
 Každý balíček má následující vlastnosti. Pokud chcete zobrazit vlastnosti, klikněte pravým tlačítkem na balíček, v diagramu nebo v Průzkumníku modelů UML a potom klikněte na **vlastnosti**.  
  
|Vlastnost|Výchozí hodnota|Popis|  
|--------------|-------------------|-----------------|  
|**Jméno**|(nové jméno)|Název balíčku. Můžete ji změnit v diagramu nebo v okně Vlastnosti.|  
|**Kvalifikovaný název**|*Kontejner* :: *název balíčku*|Celý název předchází název balíčku nebo modelu, který obsahuje tento balíček. Další informace najdete v tématu [obory názvů](#Namespaces).|  
|**Profily**|(prázdné)|Seznam profilů propojené s tímto balíčkem. Tyto profily poskytují Stereotypy, které lze použít pro prvky uvnitř balíčku. Další informace najdete v tématu [přizpůsobení modelu pomocí profilů a stereotypů](../modeling/customize-your-model-with-profiles-and-stereotypes.md).|  
|**Viditelnost**|**Public**|Viditelnost balíčku mimo jeho nadřazeného balíčku.|  
|**Pracovní položky**|(prázdné)|Seznam propojených pracovních položek. Další informace najdete v tématu [propojení prvků modelu a pracovních položek](../modeling/link-model-elements-and-work-items.md).|  
|**Umístění definice**|(název)|Název souboru, kde jsou uloženy podrobnosti o balíčku. Soubory jsou uvnitř **ModelDefinition** složky projektu. Tyto informace mohou být užitečné pro potřeby řízení zdroje.|  
|**Popis**|(prázdné)|Popis balíčku.|  
|**Stereotypy**|(prázdné)|Stereotypy, které se použijí pro tento balíček. Seznam Stereotypy, které jsou k dispozici je určený místem profily, které jste zvolili pro tento balíček a balíčky, které obsahují. Další informace najdete v tématu [přizpůsobení modelu pomocí profilů a stereotypů](../modeling/customize-your-model-with-profiles-and-stereotypes.md).|  
  
## <a name="how-packages-are-stored"></a>Ukládání balíčků  
 Při vytváření nového balíčku, nový **.uml** ve vytvoří soubor **ModelDefinition** složky projektu. Kořenového modelu, který je také balíček, je také uložena v **.uml** souboru.  
  
 Kromě toho se každý diagram je uložen ve dvou souborech, ten, který představuje do diagramu tvary a **.layout** soubor, který zaznamenává pozice tvary.  
  
## <a name="see-also"></a>Viz také  
 [Úpravy modelů a diagramů UML](../modeling/edit-uml-models-and-diagrams.md)   
 [Diagramy tříd UML: referenční dokumentace](../modeling/uml-class-diagrams-reference.md)   
 [Diagramy tříd UML: pokyny](../modeling/uml-class-diagrams-guidelines.md)   
 [Správa modelů a diagramů pomocí správy verzí](../modeling/manage-models-and-diagrams-under-version-control.md)



