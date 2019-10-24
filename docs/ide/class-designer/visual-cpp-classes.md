---
title: C++Třídy v Návrhář tříd
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.classdesigner.inheritancelinelabel
helpviewer_keywords:
- Class Designer [Visual Studio], classes
ms.assetid: 75e56f8c-11ef-42a3-b7ec-3d2cf25c581b
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: 84fc10a3f62ea4bef82a466b2d76c46e73eb7e6e
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72748931"
---
# <a name="c-classes-in-class-designer"></a>C++třídy v Návrhář tříd

**Návrhář tříd** podporuje C++ třídy a vizualizuje nativní C++ třídy stejným způsobem jako obrazce Visual Basic a C# třídy, s výjimkou toho C++ , že třídy mohou mít více vztahů dědičnosti. Můžete rozbalit obrazec třídy a zobrazit tak více polí a metod ve třídě nebo ho sbalit tak, aby ušetřilo místo.

> [!NOTE]
> **Návrhář tříd** nepodporuje sjednocení (speciální typ třídy, ve které je přidělená paměť pouze ta, která je potřebná pro největší datový člen sjednocení).

## <a name="simple-inheritance"></a>Jednoduchá dědičnost

Když přetáhnete více než jednu třídu do diagramu tříd a třídy mají vztah dědičnosti třídy, připojí se k ní šipka. Šipka směřuje do směru základní třídy. Například pokud jsou následující třídy zobrazeny v diagramu tříd, je připojena šipka, ukazující od B do:

```cpp
class A {};
class B : A {};
```

Můžete také přetáhnout pouze třídu B do diagramu tříd, kliknout pravým tlačítkem myši na obrazec třídy pro B a potom kliknout na tlačítko **Zobrazit základní třídy**. Tím se zobrazí základní třída: A.

## <a name="multiple-inheritance"></a>Vícenásobná dědičnost

**Návrhář tříd** podporuje vizualizaci vztahů dědičnosti s více třídami. *Vícenásobná dědičnost* se používá v případě, že odvozená třída má atributy více než jedné základní třídy. Následuje příklad vícenásobné dědičnosti:

```cpp
class Bird {};
class Swimmer {};
class Penguin : public Bird, public Swimmer {};
```

Když přetáhnete více než jednu třídu do diagramu tříd a třídy mají vztah dědičnosti s více třídami, připojí se šipka. Šipka směřuje do směru základních tříd.

Klikněte pravým tlačítkem myši na obrazec třídy a potom kliknutím na možnost **Zobrazit základní třídy** zobrazíte základní třídy pro vybranou třídu.

> [!NOTE]
> Příkaz **Zobrazit odvozené třídy** není pro C++ kód podporován. Odvozené třídy můžete zobrazit tak, že kliknete na **zobrazení tříd**, rozbalíte uzel typu, rozbalíte podsložku **odvozené typy** a přetáhnete tyto typy do diagramu tříd.

Další informace o dědičnosti více tříd naleznete v tématu [vícenásobná dědičnost](https://msdn.microsoft.com/library/6td5yws2.aspx) a [více základních tříd](/cpp/cpp/multiple-base-classes).

## <a name="abstract-classes"></a>Abstraktní třídy

**Návrhář tříd** podporuje abstraktní třídy (také s názvem "abstraktní základní třídy"). Jedná se o třídy, které nikdy nevytváříte, ale ze kterých můžete odvodit jiné třídy. Pomocí příkladu z "vícenásobná dědičnost" dříve v tomto dokumentu můžete vytvořit instanci `Bird` třídy jako jednotlivé objekty následujícím způsobem:

```cpp
int main()
{
   Bird sparrow;
   Bird crow;
   Bird eagle;
}
```

Nicméně nebudete mít v úmyslu vytvořit instanci `Swimmer` třídy jako jednotlivé objekty. Je možné, že máte v úmyslu odvodit jenom jiné typy tříd zvířat, například `Penguin`, `Whale` a `Fish`. V takovém případě byste třídu `Swimmer` deklarovali jako abstraktní základní třídu.

Chcete-li deklarovat třídu jako abstraktní, můžete použít klíčové slovo `abstract`. Členy označené jako abstraktní nebo zahrnuté do abstraktní třídy jsou virtuální a musí být implementované třídami odvozenými z abstraktní třídy.

```cpp
class Swimmer abstract
{
   virtual void swim();
   void dive();
};
```

Můžete také deklarovat třídu jako abstraktní zahrnutím alespoň jedné čistě virtuální funkce:

```cpp
class Swimmer
{
   virtual void swim() = 0;
   void dive();
};
```

Když zobrazíte tyto deklarace v diagramu tříd, název třídy `Swimmer` a její čistě virtuální funkce `swim` jsou zobrazeny v kurzívě v nadřazeném tvaru třídy spolu s **abstraktní třídou**Notation. Všimněte si, že obrazec typu abstraktní třídy je stejný jako u regulární třídy s tím rozdílem, že jeho ohraničení je tečkovaná čára.

Třída odvozená z abstraktní základní třídy musí přepsat každou čistě virtuální funkci v základní třídě, jinak nelze vytvořit instanci odvozené třídy. Takže pokud například odvodit třídu `Fish` z `Swimmer` třídy, `Fish` musí přepsat `swim` metoda:

```cpp
class Fish : public Swimmer
{
   void swim(int speed);
};

int main()
{
   Fish guppy;
}
```

Při zobrazení tohoto kódu v diagramu tříd **Návrhář tříd** nakreslí čáru dědičnosti z `Fish` na `Swimmer`.

## <a name="anonymous-classes"></a>Anonymní třídy

**Návrhář tříd** podporuje anonymní třídy. *Anonymní typy tříd* jsou třídy deklarované bez identifikátoru. Nemohou mít konstruktor nebo destruktor, nemohou být předány jako argumenty funkcím a nemohou být vráceny jako návratové hodnoty z funkcí. Můžete použít anonymní třídu k nahrazení názvu třídy názvem typedef, jak je uvedeno v následujícím příkladu:

```cpp
typedef struct
{
    unsigned x;
    unsigned y;
} POINT;
```

Struktury můžou být taky anonymní. **Návrhář tříd** zobrazuje anonymní třídy a struktury stejné, jako zobrazuje příslušný typ. I když můžete deklarovat a zobrazit anonymní třídy a struktury, **Návrhář tříd** nebude používat název značky, který zadáte. Bude použit název, který Zobrazení tříd generuje. Třída nebo struktura se zobrazí v Zobrazení tříd a **Návrhář tříd** jako element s názvem **__unnamed**.

Další informace o anonymních třídách naleznete v tématu [anonymní typy tříd](/cpp/cpp/anonymous-class-types).

## <a name="template-classes"></a>Třídy šablon

**Návrhář tříd** podporuje vizualizaci tříd šablon. Jsou podporovány vnořené deklarace. V následující tabulce jsou uvedeny některé typické deklarace.

| Element kódu | Zobrazení Návrhář tříd |
| - | - |
| `template <class T>`<br /><br /> `class A {};` | `A<T>`<br /><br /> Template – třída |
| `template <class T, class U>`<br /><br /> `class A {};` | `A<T, U>`<br /><br /> Template – třída |
| `template <class T, int i>`<br /><br /> `class A {};` | `A<T, i>`<br /><br /> Template – třída |
| `template <class T, template <class K> class U>`<br /><br /> `class A {};` | `A<T, U>`<br /><br /> Template – třída |

V následující tabulce jsou uvedeny některé příklady částečné specializace.

|Element kódu|Zobrazení Návrhář tříd|
|------------------| - |
|`template<class T, class U>`<br /><br /> `class A {};`|`A<T, U>`<br /><br /> Template – třída|
|`template<class T>`<br /><br /> `class A<T, T> {};`|`A<T, T>`<br /><br /> Template – třída|
|`template <class T>`<br /><br /> `class A<T, int> {};`|`A<T, int>`<br /><br /> Template – třída|
|`template <class T1, class T2>`<br /><br /> `class A<T1*, T2*> {};`|`A<T1*, T2*>`<br /><br /> Template – třída|

V následující tabulce jsou uvedeny některé příklady dědičnosti v částečné specializaci.

|Element kódu|Zobrazení Návrhář tříd|
|------------------| - |
|`template <class T, class U>`<br /><br /> `class A {};`<br /><br /> `template <class TC>`<br /><br /> `class A<T, int> {};`<br /><br /> `class B : A<int, float>`<br /><br /> `{};`<br /><br /> `class C : A<int, int>`<br /><br /> `{};`|`A<T, U>`<br /><br /> Template – třída<br /><br /> `B`<br /><br /> Třída<br /><br /> (odkazuje na třídu A)<br /><br /> `C`<br /><br /> Třída<br /><br /> (odkazuje na třídu A)|

V následující tabulce jsou uvedeny některé příklady funkcí šablon částečné specializace.

|Element kódu|Zobrazení Návrhář tříd|
|------------------| - |
|`class A`<br /><br /> `{`<br /><br /> `template <class T, class U>`<br /><br /> `void func(T a, U b);`<br /><br /> `template <class T>`<br /><br /> `void func(T a, int b);`<br /><br /> `};`|`A`<br /><br /> Func \<T, U > (+ 1 přetížení)|
|`template <class T1>`<br /><br /> `class A {`<br /><br /> `template <class T2>`<br /><br /> `class B {};`<br /><br /> `};`<br /><br /> `template<> template<>`<br /><br /> `class A<type>::B<type> {};`|`A<T1>`<br /><br /> Template – třída<br /><br /> `B<T2>`<br /><br /> Template – třída<br /><br /> (B je obsaženo v třídě A v rámci **vnořených typů**)|
|`template <class T>`<br /><br /> `class C {};`<br /><br /> `class A : C<int> {};`|`A`<br /><br /> Třída<br /><br /> -> C \<int ><br /><br /> `C<T>`<br /><br /> Template – třída|

V následující tabulce jsou uvedeny některé příklady dědičnosti šablon.

|Element kódu|Zobrazení Návrhář tříd|
|------------------| - |
|`template <class T>`<br /><br /> `class C {};`<br /><br /> `template<>`<br /><br /> `class C<int> {`<br /><br /> `class B {};`<br /><br /> `}`<br /><br /> `class A : C<int>::B {};`|`A`<br /><br /> Třída<br /><br /> – > B<br /><br /> `C<int>`<br /><br /> Třída<br /><br /> (B je obsaženo v třídě C v rámci **vnořených typů**)<br /><br /> `C<T>`<br /><br /> Template – třída|

V následující tabulce jsou uvedeny některé příklady kanonického specializovaného připojení třídy.

|Element kódu|Zobrazení Návrhář tříd|
|------------------| - |
|`template <class T>`<br /><br /> `class C {};`<br /><br /> `template<>`<br /><br /> `class C<int> {};`<br /><br /> `class A : C<int> {};`<br /><br /> `class D : C<float> {};`|`A`<br /><br /> Třída<br /><br /> -> C \<int ><br /><br /> `C<int>`<br /><br /> Třída<br /><br /> `C<T>`<br /><br /> Template – třída<br /><br /> `D`<br /><br /> Třída<br /><br /> -> C \<float >|
|`class B {`<br /><br /> `template <class T>`<br /><br /> `T min (const T &a, const T &b);`<br /><br /> `};`|`B`<br /><br /> minimální \<T >|

## <a name="see-also"></a>Viz také:

- [Práce s C++ kódem](working-with-visual-cpp-code.md)
- [Třídy a struktury](/cpp/cpp/classes-and-structs-cpp)
- [Anonymní typy tříd](/cpp/cpp/anonymous-class-types)
- [Vícenásobná dědičnost](https://msdn.microsoft.com/library/6td5yws2.aspx)
- [Vícenásobné základní třídy](/cpp/cpp/multiple-base-classes)
- [Šablony](/cpp/cpp/templates-cpp)