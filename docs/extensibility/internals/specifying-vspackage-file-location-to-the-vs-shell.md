---
title: Určení umístění souboru VSPackage do prostředí VS | Dokumenty společnosti Microsoft
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704982"
---
# <a name="specifying-vspackage-file-location-to-the-vs-shell"></a>Specifikace umístění souboru balíčku VSPackage pro prostředí sady VS
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]musí být schopen najít dll sestavení načíst VSPackage. Můžete ji najít různými způsoby, jak je popsáno v následující tabulce.

| Metoda | Popis |
| - | - |
| Použijte klíč registru CodeBase. | Klíč CodeBase lze použít [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] k přímému načtení sestavení VSPackage z libovolné plně kvalifikované cesty k souboru. Hodnota klíče by měla být cesta k dll. Toto je nejlepší [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] způsob, jak načíst sestavení balíčku. Tato technika se někdy označuje jako "CodeBase/soukromé instalační adresář technika." Při registraci je hodnota codebase předána třídám atributů <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute.RegistrationContext> registrace prostřednictvím instance typu. |
| Umístěte dll do **adresáře PrivateAssemblies.** | Umístěte sestavení do podadresáře **PrivateAssemblies** adresáře. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Sestavení umístěná v **privátnísestavení jsou** automaticky rozpoznána, ale nejsou viditelná v dialogovém okně **Přidat odkazy.** Rozdíl mezi **PrivateAssemblies** a **PublicAssemblies** spočívá v tom, že sestavení v **publicassemblies** jsou uvedena v dialogovém okně **Přidat odkazy.** Pokud jste se rozhodli nepoužívat techniku "CodeBase/private installation directory", měli byste se nainstalovat do adresáře **PrivateAssemblies.** |
| Použijte sestavení se silným názvem a klíč registru sestavení. | Klíč sestavení lze explicitně [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] nasměrovat k načtení silné pojmenované sestavení VSPackage. Hodnota klíče by měla být silný název sestavení. |
| Umístěte dll do **adresáře PublicAssemblies.** | Nakonec sestavení lze také umístit do **podadresáře PublicAssemblies.** Sestavení umístěná ve **veřejných sestaveních** jsou automaticky rozpoznána a zobrazí [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]se také v dialogovém okně Přidat **odkazy** v .<br /><br /> Sestavení VSPackage by měla být umístěna pouze v **adresáři PublicAssemblies,** pokud obsahují spravované součásti, které jsou určeny k opakovanému použití jinými vývojáři VSPackage. Většina sestavení toto kritérium nesplňuje. |

> [!NOTE]
> Používejte snopovaná podepsaná sestavení pro všechna závislá sestavení. Tato sestavení by měla být také nainstalována ve vašem vlastním adresáři nebo v globální mezipaměti sestavení (GAC). To chrání před konflikty se sestaveními, které mají stejný název základního souboru, známý jako vazba slabého názvu.
