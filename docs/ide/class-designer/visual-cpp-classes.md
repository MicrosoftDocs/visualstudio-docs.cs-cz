---
title: Třídy C++ v Návrháři tříd
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.classdesigner.inheritancelinelabel
helpviewer_keywords:
- Class Designer [Visual Studio], classes
ms.assetid: 75e56f8c-11ef-42a3-b7ec-3d2cf25c581b
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: d68391bbd4c6c873940bbc2714ee41db8309b629
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75590732"
---
# <a name="c-classes-in-class-designer"></a>Třídy C++ v Návrháři tříd

**Návrhář tříd** podporuje třídy Jazyka C++ a vizualizuje nativní třídy Jazyka C++ stejným způsobem jako obrazce tříd visual basic a C#, s tím rozdílem, že třídy Jazyka C++ mohou mít více vztahů dědičnosti. Chcete-li ušetřit místo, můžete rozšířit obrazec třídy tak, aby zobrazoval více polí a metod ve třídě, nebo jej sbalit.

> [!NOTE]
> **Návrhář třídy** nepodporuje sjednocení (zvláštní typ třídy, ve kterém přidělené paměti je pouze částka potřebná pro největší datový člen unie).

## <a name="simple-inheritance"></a>Jednoduchá dědičnost

Když přetáhnete více než jednu třídu do diagramu třídy a třídy mají vztah dědičnosti třídy, propojí je šipka. Šipka ukazuje ve směru základní třídy. Pokud jsou například v diagramu třídy zobrazeny následující třídy, propojí je šipka směřující z bodu B do Bodu A:

```cpp
class A {};
class B : A {};
```

Můžete také přetáhnout pouze třídu B do diagramu třídy, klepnout pravým tlačítkem myši na obrazec třídy pro B a potom kliknout na **zobrazit základní třídy**. Zobrazí se základní třída: A.

## <a name="multiple-inheritance"></a>Vícenásobná dědičnost

**Návrhář tříd** podporuje vizualizaci vícetřídních vztahů dědičnosti. *Vícedědičnost* se používá, když odvozené třídy má atributy více než jednu základní třídu. Následuje příklad vícenásobné dědičnosti:

```cpp
class Bird {};
class Swimmer {};
class Penguin : public Bird, public Swimmer {};
```

Když přetáhnete více než jednu třídu do diagramu třídy a třídy mají vztah dědičnosti více tříd, propojí je šipka. Šipka ukazuje ve směru základní třídy.

Kliknutím pravým tlačítkem myši na obrazec třídy a následným klepnutím na **příkaz Zobrazit základní třídy** se zobrazí základní třídy pro vybranou třídu.

> [!NOTE]
> Příkaz **Zobrazit odvozené třídy** není pro kód jazyka C++ podporován. Odvozené třídy můžete zobrazit tak, že přejdete do **zobrazení třídy**, rozbalíte uzel typu, rozbalíte podsložku **Odvozené typy** a pak tyto typy přetáhnete do diagramu třídy.

Další informace o dědičnosti více tříd naleznete [v tématu Vícenásobná dědičnost](https://msdn.microsoft.com/library/6td5yws2.aspx) a [Více základních tříd](/cpp/cpp/multiple-base-classes).

## <a name="abstract-classes"></a>Abstraktní třídy

**Návrhář tříd** podporuje abstraktní třídy (také s názvem "abstraktní základní třídy"). Jedná se o třídy, které nikdy konkretizovat, ale ze kterých můžete odvodit jiné třídy. Pomocí příkladu z "Vícedědičnosti" dříve v tomto dokumentu `Bird` můžete vytvořit konkretizovat třídu jako jednotlivé objekty následujícím způsobem:

```cpp
int main()
{
   Bird sparrow;
   Bird crow;
   Bird eagle;
}
```

Však nemusí mít v úmyslu vytvořit `Swimmer` konkretizovat třídy jako jednotlivé objekty. Můžete z něj chtít odvodit pouze jiné `Penguin`druhy `Whale`tříd `Fish`zvířat, například , , a . V takovém případě byste `Swimmer` deklarovat třídu jako abstraktní základní třídy.

Chcete-li deklarovat třídu `abstract` jako abstraktní, můžete použít klíčové slovo. Členové označeny jako abstraktní nebo zahrnuty do abstraktní třídy jsou virtuální a musí být implementovány třídy, které jsou odvozeny z abstraktní třídy.

```cpp
class Swimmer abstract
{
   virtual void swim();
   void dive();
};
```

Můžete také deklarovat třídu jako abstraktní zahrnutím alespoň jedné čisté virtuální funkce:

```cpp
class Swimmer
{
   virtual void swim() = 0;
   void dive();
};
```

Při zobrazení těchto deklarací v diagramu `Swimmer` třídy název `swim` třídy a jeho čisté virtuální funkce jsou zobrazeny kurzívou v obrazci abstraktní třídy, spolu s notace **Abstraktní třídy**. Všimněte si, že tvar abstraktního typu třídy je stejný jako u běžné třídy s tím rozdílem, že jeho ohraničení je tečkovaná čára.

Třída odvozená z abstraktní základní třídy musí přepsat každou čistou virtuální funkci v základní třídě nebo odvozenou třídu nelze vytvořit instanci. Takže například pokud `Fish` odvodit `Swimmer` třídu `Fish` z třídy, musí přepsat metodu: `swim`

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

Při zobrazení tohoto kódu v diagramu tříd, Návrhář `Fish` `Swimmer` **tříd** nakreslí řádek dědičnosti z do .

## <a name="anonymous-classes"></a>Anonymní třídy

**Návrhář tříd** podporuje anonymní třídy. *Anonymní typy tříd* jsou třídy deklarované bez identifikátoru. Nemohou mít konstruktor nebo destruktor, nemohou být předány jako argumenty funkcím a nemohou být vráceny jako vrácené hodnoty z funkcí. Anonymní třídu můžete použít k nahrazení názvu třídy názvem typedef, jako v následujícím příkladu:

```cpp
typedef struct
{
    unsigned x;
    unsigned y;
} POINT;
```

Struktury mohou být také anonymní. **Návrhář tříd** zobrazuje anonymní třídy a struktury stejné jako zobrazuje příslušný typ. Přestože můžete deklarovat a zobrazit anonymní třídy a struktury, **Návrhář tříd** nebude používat název značky, který zadáte. Bude používat název, který generuje zobrazení třídy. Třída nebo struktura se zobrazí v zobrazení třídy a **Návrhář epoje třídy** jako prvek s názvem **__unnamed**.

Další informace o anonymních třídách naleznete [v tématu Anonymous Class Types](/cpp/cpp/anonymous-class-types).

## <a name="template-classes"></a>Třídy šablon

**Návrhář tříd** podporuje vizualizaci tříd šablon. Vnořené deklarace jsou podporovány. V následující tabulce jsou uvedeny některé typické deklarace.

| Element kódu | Zobrazení Návrháře tříd |
| - | - |
| `template <class T>`<br /><br /> `class A {};` | `A<T>`<br /><br /> Třída šablony |
| `template <class T, class U>`<br /><br /> `class A {};` | `A<T, U>`<br /><br /> Třída šablony |
| `template <class T, int i>`<br /><br /> `class A {};` | `A<T, i>`<br /><br /> Třída šablony |
| `template <class T, template <class K> class U>`<br /><br /> `class A {};` | `A<T, U>`<br /><br /> Třída šablony |

V následující tabulce jsou uvedeny některé příklady částečné specializace.

|Element kódu|Zobrazení Návrháře tříd|
|------------------| - |
|`template<class T, class U>`<br /><br /> `class A {};`|`A<T, U>`<br /><br /> Třída šablony|
|`template<class T>`<br /><br /> `class A<T, T> {};`|`A<T, T>`<br /><br /> Třída šablony|
|`template <class T>`<br /><br /> `class A<T, int> {};`|`A<T, int>`<br /><br /> Třída šablony|
|`template <class T1, class T2>`<br /><br /> `class A<T1*, T2*> {};`|`A<T1*, T2*>`<br /><br /> Třída šablony|

V následující tabulce jsou uvedeny některé příklady dědičnosti v částečné specializaci.

|Element kódu|Zobrazení Návrháře tříd|
|------------------| - |
|`template <class T, class U>`<br /><br /> `class A {};`<br /><br /> `template <class TC>`<br /><br /> `class A<T, int> {};`<br /><br /> `class B : A<int, float>`<br /><br /> `{};`<br /><br /> `class C : A<int, int>`<br /><br /> `{};`|`A<T, U>`<br /><br /> Třída šablony<br /><br /> `B`<br /><br /> Třída<br /><br /> (body třídy A)<br /><br /> `C`<br /><br /> Třída<br /><br /> (body třídy A)|

V následující tabulce jsou uvedeny některé příklady funkcí šablony částečné specializace.

|Element kódu|Zobrazení Návrháře tříd|
|------------------| - |
|`class A`<br /><br /> `{`<br /><br /> `template <class T, class U>`<br /><br /> `void func(T a, U b);`<br /><br /> `template <class T>`<br /><br /> `void func(T a, int b);`<br /><br /> `};`|`A`<br /><br /> func\<T, U> (+ 1 přetížení)|
|`template <class T1>`<br /><br /> `class A {`<br /><br /> `template <class T2>`<br /><br /> `class B {};`<br /><br /> `};`<br /><br /> `template<> template<>`<br /><br /> `class A<type>::B<type> {};`|`A<T1>`<br /><br /> Třída šablony<br /><br /> `B<T2>`<br /><br /> Třída šablony<br /><br /> (B je obsaženve třídě A pod **vnořené typy**)|
|`template <class T>`<br /><br /> `class C {};`<br /><br /> `class A : C<int> {};`|`A`<br /><br /> Třída<br /><br /> ->\<C int><br /><br /> `C<T>`<br /><br /> Třída šablony|

V následující tabulce jsou uvedeny některé příklady dědičnosti šablony.

|Element kódu|Zobrazení Návrháře tříd|
|------------------| - |
|`template <class T>`<br /><br /> `class C {};`<br /><br /> `template<>`<br /><br /> `class C<int> {`<br /><br /> `class B {};`<br /><br /> `}`<br /><br /> `class A : C<int>::B {};`|`A`<br /><br /> Třída<br /><br /> ->B<br /><br /> `C<int>`<br /><br /> Třída<br /><br /> (B je obsažena ve třídě C pod **vnořené typy**)<br /><br /> `C<T>`<br /><br /> Třída šablony|

V následující tabulce jsou uvedeny některé příklady připojení kanonické specializované třídy.

|Element kódu|Zobrazení Návrháře tříd|
|------------------| - |
|`template <class T>`<br /><br /> `class C {};`<br /><br /> `template<>`<br /><br /> `class C<int> {};`<br /><br /> `class A : C<int> {};`<br /><br /> `class D : C<float> {};`|`A`<br /><br /> Třída<br /><br /> ->\<C int><br /><br /> `C<int>`<br /><br /> Třída<br /><br /> `C<T>`<br /><br /> Třída šablony<br /><br /> `D`<br /><br /> Třída<br /><br /> ->\<C plovákový>|
|`class B {`<br /><br /> `template <class T>`<br /><br /> `T min (const T &a, const T &b);`<br /><br /> `};`|`B`<br /><br /> min \<T>|

## <a name="see-also"></a>Viz také

- [Práce s kódem jazyka C++](working-with-visual-cpp-code.md)
- [Třídy a struky](/cpp/cpp/classes-and-structs-cpp)
- [Anonymní typy třídy](/cpp/cpp/anonymous-class-types)
- [Vícenásobná dědičnost](https://msdn.microsoft.com/library/6td5yws2.aspx)
- [Vícenásobné základní třídy](/cpp/cpp/multiple-base-classes)
- [Šablony](/cpp/cpp/templates-cpp)
