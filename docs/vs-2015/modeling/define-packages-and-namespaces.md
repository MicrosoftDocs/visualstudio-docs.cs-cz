---
title: Definování balíčků a oborů názvů | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- UML model, namespaces
- UML, namespaces
- UML, packages
- UML model, packages
ms.assetid: 79147068-02d5-4b70-933d-f647c1da3829
caps.latest.revision: 22
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 657bb91295134352fb00649ad06f59e34593c578
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72669906"
---
# <a name="define-packages-and-namespaces"></a>Definování balíčků a oborů názvů
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

V aplikaci Visual Studio je *balíček* kontejner pro definice prvků UML, jako jsou třídy, případy použití a součásti. Balíček může obsahovat i další balíčky.

 V Průzkumníku modelů UML jsou všechny definice uvnitř balíčku vnořené pod balíčkem. Model UML je druh balíčku a tvoří kořen stromu.

 Chcete-li zjistit, které verze aplikace Visual Studio tuto funkci podporují, přečtěte si téma [podpora verzí pro nástroje pro architekturu a modelování](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

## <a name="in-this-topic"></a>V tomto tématu
 [Obory názvů](#Namespaces)

 [Vytváření a zobrazování balíčků](#Packages)

 [Vytváření elementů modelu uvnitř balíčků](#Elements)

 [Přesun prvků do balíčku nebo z něj](#Moving)

 [Vkládání elementů do balíčku](#Pasting)

 [Import vztahů mezi balíčky](#Import)

 [Odkazy z jednoho oboru názvů na jiný](#References)

 [Vlastnosti balíčků](#Properties)

## <a name="Namespaces"></a>Obsažené
 Balíčky jsou užitečné pro oddělení práce do různých oblastí. Každý balíček definuje obor názvů tak, aby názvy, které jsou definovány v různých balíčcích, nebyly vzájemně v konfliktu.

 Vlastnost kvalifikovaného názvu každého prvku je kvalifikovaný název balíčku, ke kterému patří, následovaný vlastním názvem elementu. Například pokud se balíček nazývá `MyPackage`, třída v rámci balíčku bude mít kvalifikovaný název jako `MyPackage::MyClass`. Vzhledem k tomu, že každý element je obsažen v modelu, každý kvalifikovaný název začíná názvem modelu.

 Model také definuje obor názvů, takže kvalifikovaný název každého prvku v modelu začíná názvem modelu.

 Jiné prvky modelu také definují obory názvů. Například operace patří k oboru názvů definovanému jeho nadřazenou třídou, aby byl jeho kvalifikovaný název například `MyModel ::MyPackage ::MyClass ::MyOperation`. Stejným způsobem patří akce do oboru názvů, který definuje jeho Nadřazená aktivita.

 Balíčky jsou kontejnery. Při přesunutí nebo odstranění balíčku se přesunou nebo odstraní také třídy, balíčky a další objekty, které jsou v něm definovány. Totéž platí i pro ostatní prvky, které definují obory názvů.

## <a name="Packages"></a>Vytváření a zobrazování balíčků
 Balíček můžete vytvořit buď v diagramu tříd UML, nebo v Průzkumníku modelů UML.

#### <a name="to-create-a-package-in-a-uml-class-diagram"></a>Vytvoření balíčku v diagramu tříd UML

1. Otevřete diagram tříd UML nebo vytvořte nový.

2. Klikněte na nástroj **balíček** .

3. Klikněte kamkoli do diagramu. Zobrazí se nový obrazec balíčku.

     Můžete kliknout na existující balíček a vnořit jeden balíček do jiného.

4. Zadejte nový název balíčku.

#### <a name="to-create-a-package-in-uml-model-explorer"></a>Vytvoření balíčku v Průzkumníkovi modelů UML

1. Otevřete **Průzkumníka modelů UML**. V nabídce **Architektura** přejděte na **okna**a potom klikněte na **Průzkumník modelů UML**.

2. Klikněte pravým tlačítkem na balíček nebo model, ke kterému chcete přidat nový balíček.

   > [!NOTE]
   > Balíček můžete vnořit do jiného balíčku.

3. Přejděte na **Přidat** a pak klikněte na **balíček**.

    V modelu se zobrazí nový balíček.

4. Zadejte nový název balíčku.

   Pokud jste balíček vytvořili v Průzkumníku modelů UML, můžete jej zobrazit v diagramu tříd UML. Balíček můžete také zobrazit ve více než jednom diagramu tříd UML.

#### <a name="to-show-an-existing-package-on-a-uml-class-diagram"></a>Zobrazení existujícího balíčku v diagramu tříd UML

- Přetáhněte balíček z Průzkumníka modelů UML do diagramu tříd.

    > [!NOTE]
    > Tím se vytvoří zobrazení balíčku na tomto diagramu. Nebude nutně zobrazovat všechny prvky, které balíček obsahuje. Abyste se ujistili, že vidíte obsah balíčku, zobrazte ho v Průzkumníku modelů UML.

## <a name="Elements"></a>Vytváření elementů modelu uvnitř balíčků
 Existují čtyři způsoby, jak lze umístit prvky modelu do balíčku:

- Přidá nový prvek do balíčku v Průzkumníku modelů UML.

- Přidejte třídy a další typy do balíčků v diagramu tříd UML.

- Nastavte vlastnost **LinkedPackage** diagramu tak, aby se nové prvky vytvořené v diagramu umístily do balíčku, který zadáte. Diagramy tříd, diagramy komponent a diagramy použití lze tímto způsobem propojit s balíčkem.

- Přesune prvky do nebo ven z balíčku v Průzkumníku modelů UML.

  Element v balíčku se v Průzkumníku modelů UML zobrazuje pod balíčkem a jeho kvalifikovaný název začíná úplným názvem balíčku. Chcete-li zobrazit kvalifikovaný název libovolného prvku, klikněte na něj pravým tlačítkem myši a potom klikněte na příkaz **vlastnosti**. Vlastnost **kvalifikovaného názvu** se zobrazí v okně **vlastnosti** .

#### <a name="to-create-an-element-in-a-package-in-uml-model-explorer"></a>Vytvoření prvku v balíčku v Průzkumníkovi modelů UML

1. Otevřete **Průzkumníka modelů UML**. V nabídce **zobrazení** přejděte na položku **ostatní okna**a klikněte na možnost **Průzkumník modelů UML**.

2. Klikněte pravým tlačítkem na balíček nebo model, ke kterému chcete přidat nový prvek.

3. Přejděte na **Přidat**a potom klikněte na druh prvku, který chcete přidat.

     Nový prvek se zobrazí pod balíčkem.

4. Zadejte název nového elementu.

    > [!NOTE]
    > Nový prvek se nezobrazuje na žádném diagramu. Chcete-li vytvořit zobrazení nového prvku, můžete jej přetáhnout z Průzkumníka modelů UML do diagramu. Diagram musí být typ, který zobrazí tento druh prvku.

#### <a name="to-create-an-element-in-a-package-on-a-uml-class-diagram"></a>Vytvoření prvku v balíčku v diagramu tříd UML

1. Otevřete diagram třídy, na kterém se balíček zobrazuje.

    - Vytvořte nový balíček, pokud jste to ještě neudělali.

    - Chcete-li vytvořit existující balíček v diagramu tříd, můžete jej přetáhnout z **Průzkumníka modelů UML** do diagramu tříd.

2. Klikněte na nástroj pro třídu, rozhraní nebo výčet nebo na balíček.

3. Klikněte na balíček, kam chcete vložit nový prvek.

     Nový prvek se zobrazí uvnitř balíčku.

#### <a name="to-create-all-the-elements-of-a-diagram-in-a-specified-package"></a>Vytvoření všech prvků diagramu v zadaném balíčku

1. Vytvořte balíček, pokud jste to ještě neudělali.

2. Otevřete diagram komponent, diagram případu použití nebo diagram tříd UML.

3. Otevřete vlastnosti diagramu. Klikněte pravým tlačítkem na prázdnou část diagramu a pak klikněte na **vlastnosti**.

4. Ve vlastnosti **propojený balíček** vyberte balíček, který chcete, aby obsahoval obsah diagramu.

5. V diagramu vytvořte nové prvky. Budou umístěny do balíčku.

    - **Kvalifikovaný** název každého elementu bude začínat kvalifikovaným názvem balíčku.

    - V **Průzkumníku modelů UML**se každý prvek zobrazí v rámci balíčku.

## <a name="Moving"></a>Přesun prvků do balíčků a z nich
 Jeden nebo více prvků můžete přesunout do balíčku nebo z něj.

 Pokud balíček přesunete, vše uvnitř něj se přesune s ním.

#### <a name="to-move-an-element-into-or-out-of-a-package"></a>Přesunutí elementu do nebo ven z balíčku

- V Průzkumníku modelů UML přetáhněte prvek do stromové struktury, jejíž kořen je balíček.

     Kvalifikovaný název elementu se změní tak, aby zobrazoval jeho nový vlastnící balíček nebo model.

     \- nebo-

- V diagramu tříd přetáhněte prvek do obrazce balíčku.

     Kvalifikovaný název elementu se změní tak, aby zobrazoval jeho nový vlastnící balíček.

    > [!NOTE]
    > Pokud přetáhnete prvek z balíčku do prázdné části diagramu, jeho vlastnící balíček se nezmění. To vám umožní vytvořit diagram, který zobrazuje elementy z několika balíčků bez nutnosti zobrazit samotné balíčky.

## <a name="Pasting"></a>Vkládání elementů do balíčku
 Do balíčku můžete vložit element. Pokud do balíčku vložíte skupinu souvisejících prvků, budou také vloženy relace mezi nimi.

#### <a name="to-paste-elements-into-a-package-on-a-uml-class-diagram"></a>Vložení prvků do balíčku v diagramu tříd UML

1. V diagramu tříd UML vyberte všechny prvky, které chcete kopírovat. Klikněte na jednu z nich pravým tlačítkem myši a pak klikněte na **Kopírovat**.

2. Klikněte pravým tlačítkem na balíček a pak klikněte na **Vložit**.

    > [!NOTE]
    > Balíček může být v jiném diagramu.

## <a name="Import"></a>Import vztahů mezi balíčky
 Můžete definovat relaci importu mezi balíčky pomocí nástroje pro **Import** .

 Import znamená, že prvky definované v importovaném balíčku, které jsou prvky na konci relace, jsou efektivně definovány také v importovaném balíčku. Všechny prvky, jejichž viditelnost je definovaná jako **Package** , se zobrazí také v importovaném balíčku.

 Vyhněte se vytváření smyček v relacích importu.

## <a name="References"></a>Odkazy z jednoho oboru názvů na jiný
 Pokud chcete odkazovat na prvek jednoho balíčku z jiného, je nutné použít kvalifikovaný název elementu.

 Předpokládejme například, že balíček `SalesCommon` definuje typ `CustomerAddress`. V jiném `RestaurantSales` balíčku chcete definovat typ `MealOrder`, který má atribut typu adresa zákazníka. Máte dvě možnosti:

- Zadejte typ atributu pomocí plně kvalifikovaného názvu `SalesCommon::CustomerAddress`. To byste měli udělat, jenom když `CustomerAddress` má vlastnost **visibility** nastavenou na **Public**.

- Vytvořte vztah importu z balíčku `RestaurantSales` do balíčku `SalesCommon`. Pak můžete použít `CustomerAddress` bez použití jeho kvalifikovaného názvu.

## <a name="Properties"></a>Vlastnosti balíčků
 Každý balíček má následující vlastnosti. Vlastnosti zobrazíte tak, že kliknete pravým tlačítkem na balíček, a to buď v diagramu, nebo v Průzkumníku modelů UML, a potom kliknete na **vlastnosti**.

|Vlastnost|Výchozí hodnota|Popis|
|--------------|-------------------|-----------------|
|**Jméno**|(nový název)|Název balíčku Můžete ho změnit buď v diagramu, nebo v okno Vlastnosti.|
|**Kvalifikovaný název**|*Kontejner* :: *název balíčku*|Celé jméno, které je předponou názvu balíčku nebo modelu, který obsahuje tento balíček. Další informace najdete v tématu [obory názvů](#Namespaces).|
|**Uživatelů**|obsahovat|Seznam profilů, které jsou propojeny s tímto balíčkem. Tyto profily poskytují stereotypy, které lze použít na prvky uvnitř balíčku. Další informace najdete v tématu [Přizpůsobení modelu pomocí profilů a stereotypů](../modeling/customize-your-model-with-profiles-and-stereotypes.md).|
|**Viditelnost**|**Public**|Viditelnost balíčku je mimo jeho nadřazený balíček.|
|**Pracovní položky**|obsahovat|Seznam propojených pracovních položek. Další informace naleznete v tématu [propojování prvků modelu a pracovních položek](../modeling/link-model-elements-and-work-items.md).|
|**Umístění definice**|(název)|Název souboru, ve kterém jsou uloženy podrobnosti balíčku. Soubory jsou umístěny ve složce projektu **ModelDefinition** . Tyto informace mohou být užitečné pro účely správy zdrojového kódu.|
|**Popis**|obsahovat|Popis balíčku|
|**Stereotypy**|obsahovat|Stereotypy, které jsou aplikovány na tento balíček. Seznam stereotypů, které jsou k dispozici, jsou určeny profily, které jste zvolili pro tento balíček a balíčky, které jej obsahují. Další informace najdete v tématu [Přizpůsobení modelu pomocí profilů a stereotypů](../modeling/customize-your-model-with-profiles-and-stereotypes.md).|

## <a name="how-packages-are-stored"></a>Jak se ukládají balíčky
 Při vytváření nového balíčku se vytvoří nový soubor **. UML** ve složce projektu **ModelDefinition** . Kořenový model, který je také balíček, je uložen také v souboru **. UML** .

 Kromě toho je každý diagram uložen ve dvou souborech, jeden, který představuje obrazce diagramu, a soubor **. Layout** , který zaznamenává pozice obrazců.

## <a name="see-also"></a>Viz také
 [Upravit modely a diagramy UML](../modeling/edit-uml-models-and-diagrams.md) diagramy [tříd UML: referenční](../modeling/uml-class-diagrams-reference.md) [diagramy tříd UML: pokyny](../modeling/uml-class-diagrams-guidelines.md) pro [správu modelů a diagramů v rámci správy verzí](../modeling/manage-models-and-diagrams-under-version-control.md)
