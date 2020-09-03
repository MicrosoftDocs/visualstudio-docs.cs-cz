---
title: Přizpůsobení modelu pomocí profilů a stereotypů | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- UML model, profiles
- UML model, stereotypes
- UML model, customizing
ms.assetid: fd607157-0d3a-4583-a84e-427a4b2a5acb
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: b634b11418ef2d4220dc4eb07c825b514ab5494c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "74301197"
---
# <a name="customize-your-model-with-profiles-and-stereotypes"></a>Přizpůsobení modelu pomocí profilů a stereotypů
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

V aplikaci Visual Studio můžete upravit standardní prvky modelu UML, jako jsou třídy a komponenty, abyste je mohli přizpůsobit pro konkrétní účely. *Stereotyp* lze použít na prvek modelu, který může změnit seznam vlastností elementu. Stereotypy jsou definovány v rámci kolekcí nazývaných *profily*.

 Chcete-li zjistit, které verze aplikace Visual Studio tuto funkci podporují, přečtěte si téma [podpora verzí pro nástroje pro architekturu a modelování](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

 Chcete-li použít stereotyp, propojíte balíček s profilem. To umožňuje použít stereotypy, které jsou definovány v profilu, na prvky v balíčku. Některé profily jsou nainstalovány společně se sadou Visual Studio. Kromě toho můžete definovat vlastní profily.

 Stereotypy lze nastavit v seznamu vlastností elementu. U hlavních druhů tvarů v diagramu se použité stereotypy zobrazí také v obrazci, jak je znázorněno v příkladu.

 ![Třída UML se stereotypem](../modeling/media/uml-class-stereotype.png "UML_class_stereotype")

> [!NOTE]
> Pokud k vytvoření modelu použijete profil a potom model nasdílíte s někým jiným, nebudou se tyto stereotypy zobrazovat, pokud na jejich počítači nenainstalujete stejný profil.

## <a name="related-topics"></a>Související témata

|Nadpis|Popis|
|-----------|-----------------|
|[Přidávání stereotypů k elementům modelu UML](../modeling/add-stereotypes-to-uml-model-elements.md)|Umístění prvku modelu do balíčku, propojení balíčku s profilem a použití stereotypu k elementu.|
|[Standardní stereotypy pro modely UML](../modeling/standard-stereotypes-for-uml-models.md)|Standard UML profily L2 a L3 se instalují se sadou Visual Studio a každý model je ve výchozím nastavení propojený s nimi. Poskytují stereotypy, které můžete použít k přidání poznámek k vašim modelům.<br /><br /> Například můžete použít stereotyp «Specification» na třídu, která označuje, že je určena pouze k definování externě viditelného chování instancí,|
|[Definování profilu pro rozšíření UML](../modeling/define-a-profile-to-extend-uml.md)|Můžete definovat vlastní stereotypy a nástroje, které jsou přizpůsobené vaší vlastní oblasti aplikace.<br /><br /> Pokud například vyvíjíte bankovní software, můžete definovat stereotyp «účet», který lze použít na třídy. Pak můžete použít diagramy tříd k popisu různých typů účtu a jejich vztahů.|
|[Instalace profilu UML](../modeling/install-a-uml-profile.md)|Pokud vám někdo dal profil UML, můžete ho nainstalovat do svého počítače.|
|[Definování vlastní položky sady nástrojů pro modelování](../modeling/define-a-custom-modeling-toolbox-item.md)|Vlastní položka sady nástrojů vám ušetří v opakovaném nastavení stereotypu pro nové prvky.|
