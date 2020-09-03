---
title: Určení umístění souboru VSPackage do prostředí VS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- managed VSPackages, file location
- VSPackages, managed package file location
ms.assetid: beb8607a-4183-4ed2-9ac8-7527f11513b1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f112da4e79bff06d12472f0af7a3fe47b2f25da4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "80704982"
---
# <a name="specifying-vspackage-file-location-to-the-vs-shell"></a>Specifikace umístění souboru balíčku VSPackage pro prostředí sady VS
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] musí být schopné najít knihovnu DLL sestavení pro načtení VSPackage. Můžete ji vyhledat různými způsoby, jak je popsáno v následující tabulce.

| Metoda | Popis |
| - | - |
| Použijte klíč registru CodeBase. | Klíč CodeBase lze použít k přímému [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] načtení sestavení VSPackage z jakékoli plně kvalifikované cesty k souboru. Hodnota klíče by měla být cesta k souboru DLL. Toto je nejlepší způsob, jak [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] načíst sestavení balíčku. Tato technika se někdy označuje jako "metoda instalačního adresáře pro základ kódu/privátní." Během registrace se hodnota základu kódu předává do tříd registračních atributů prostřednictvím instance <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute.RegistrationContext> typu. |
| Uložte knihovnu DLL do adresáře **PrivateAssemblies** . | Sestavení umístěte do podadresáře **PrivateAssemblies** [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] adresáře. Sestavení umístěná v **PrivateAssemblies** se automaticky zjišťují, ale nejsou viditelná v dialogovém okně **Přidat odkazy** . Rozdíl mezi **PrivateAssemblies** a **PublicAssemblies** je, že sestavení v **PublicAssemblies** jsou v dialogovém okně **Přidat odkazy** výčtu. Pokud se rozhodnete, že nepoužijete techniku "CodeBase/Private instalační adresář", měli byste nainstalovat do adresáře **PrivateAssemblies** . |
| Použijte sestavení se silným názvem a klíč registru sestavení. | Klíč sestavení lze použít k explicitnímu přímému [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] načtení silného pojmenovaného sestavení VSPackage. Hodnota klíče by měla být silného názvu sestavení. |
| Uložte knihovnu DLL do adresáře **PublicAssemblies** . | Nakonec může být sestavení také umístěno do podadresáře **PublicAssemblies** . Sestavení umístěná v **PublicAssemblies** se automaticky zjišťují a zobrazí se také v dialogovém okně **Přidat odkazy** v [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .<br /><br /> Sestavení VSPackage by mělo být umístěno pouze v adresáři **PublicAssemblies** , pokud obsahují spravované součásti, které mají být použity jiným vývojářům VSPackage. Většina sestavení nesplňuje toto kritérium. |

> [!NOTE]
> Používejte podepsaná sestavení se silným názvem pro všechna vaše závislá sestavení. Tato sestavení by také měla být nainstalována ve vašem vlastním adresáři nebo globální mezipaměti sestavení (GAC). To je chráněno proti konfliktům se sestaveními, která mají stejný základní název souboru, označovaného jako vytvoření vazby se slabým názvem.
