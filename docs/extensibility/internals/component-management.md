---
title: Správa komponent | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- installation [Visual Studio SDK], components
- installation [Visual Studio SDK], file management
ms.assetid: 029bffa2-6841-4caa-a41a-442467e1aedc
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b5dcac9fb14a83021b852be2c52436fcdca84bf5
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709327"
---
# <a name="component-management"></a>Správa komponent
Jednotky úloh v Instalační službě systému Windows jsou označovány jako součásti Instalační služby systému Windows (někdy nazývané WiC nebo pouze součásti). Identifikátor GUID identifikuje každý wic, což je základní jednotka instalace a počítání odkazů pro nastavení, která používají Instalační službu systému Windows.

 Přestože k vytvoření instalačního programu VSPackage můžete použít několik produktů, tato diskuse předpokládá použití souborů Instalační služby systému Windows (*MSI*). Při vytváření instalačního programu je nutné správně spravovat nasazení souborů, aby vždy nastat správné počítání odkazů. V důsledku toho různé verze produktu nebudou vzájemně zasahovat ani se vzájemně rozbít v kombinaci scénářů instalace a odinstalace.

 V Instalační službě systému Windows dochází k počítání odkazů na úrovni komponenty. Je nutné pečlivě uspořádat prostředky – soubory, položky registru a tak dále – do součástí. Existují i jiné úrovně organizace , které mohou pomoci v různých scénářích. Další informace naleznete v [tématu Základy Instalační služby systému Windows](../../extensibility/internals/windows-installer-basics.md).

## <a name="guidelines-of-authoring-setup-for-side-by-side-installation"></a>Pokyny pro vytváření nastavení pro souběžnou instalaci

- Autor soubory a klíče registru, které jsou sdíleny mezi verzemi do svých vlastních součástí.

     To vám umožní snadno je konzumovat v další verzi. Například knihovny typů, které jsou registrovány globálně, přípony souborů, další položky registrované v **HKEY_CLASSES_ROOT**a tak dále.

- Seskupte sdílené součásti do samostatných slučovacích modulů.

     Tato strategie vám pomůže správně vytvářet pro souběžné instalace vpřed.

- Nainstalujte sdílené soubory a klíče registru pomocí stejných součástí Instalační služby systému Windows v různých verzích.

     Pokud používáte jinou komponentu, soubory a položky registru jsou odinstalovány, když je odinstalován jeden vsed verze VSPackage, ale jiný VSPackage je stále nainstalován.

- Nemíchejte verze a sdílené položky ve stejné součásti.

     Tím znemožňujete instalaci sdílených položek do globálního umístění a položek s verzí do izolovaných umístění.

- Nemáte sdílené klíče registru, které odkazují na soubory s verzí.

     Pokud tak učiníte, sdílené klíče budou přepsány při instalaci jiné verze VSPackage. Po odebrání druhé verze je soubor, na který klíč ukazuje, pryč.

## <a name="see-also"></a>Viz také
- [Výběr mezi sdílenými a verzemi vs balíčků](../../extensibility/choosing-between-shared-and-versioned-vspackages.md)
- [Scénáře instalace balíčku VSPackage](../../extensibility/internals/vspackage-setup-scenarios.md)
