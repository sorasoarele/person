?php

interface IFamily
{
  public function setFirstName($fistName);
  public function getFirstName();
  public function setLastName($lastName);
  public function getLastName();
  public function setAge($age);
  public function getAge();
  public function setMother($mother);
  public function getMother();
  public function setFather($father);
  public function getFather();
}
class Person implements IFamily
{
  private $firstName;
  private $lastName;
  private $age;
  private $mother;
  private $father;
  private $hp;

  function __construct($firstName, $lastName, $age, $mother = null, $father = null)
  {
    $this->setFirstName($firstName);
    $this->setLastName($lastName);
    $this->setAge($age);
    $this->setMother($mother);
    $this->setFather($father);
    $this->hp = 100;
  }
  function setFirstName($firstName)
  {
    $this->firstName = $firstName;
  }
  function getFirstName()
  {
    return $this->firstName;
  }
  function setLastName($lastName)
  {
    $this->lastName = $lastName;
  }
  function getLastName()
  {
    return $this->lastName;
  }
  function setAge($age)
  {
    $this->age = $age > 110 ? 110 : $age;
  }
  function getAge()
  {
    return $this->age;
  }
  function setMother($mother)
  {
    if ($mother instanceof IFamily or $mother != null) {
      $this->mother = $mother;
    }
  }
  function getMother()
  {
    return $this->mother;
  }
  function setFather($father)
  {
    if ($father instanceof IFamily or $father != null) {
      $this->father = $father;
    }
  }
  function getFather()
  {
    return $this->father;
  }
  function getHp()
  {
    return $this->hp;
  }
  function getFullName()
  {
    return $this->firstName . ", " . $this->lastName;
  }
}

$gfMisha = new Person("Миша", "Крабов", 70);
$gmLuba = new Person("Люба", "Крaбова", 64);

$gfAnton = new Person("Антон", "Мазур", 65);
$gmVera = new Person("Вера", "Мазур", 65);

$fAlex = new Person("Алексей", "Мазур", 43, $gmVera, $gfAnton);
$mIкa = new Person("Иpа", "Мазур", 43, $gmLuba, $gfMisha);

$sAndrey = new Person("Андрей", "Мазур", 10, $mIra, $fAlex);
$dAnna = new Person("Анна", "Мазур", 11, $mIra, $fAlex);

echo "Привет!, меня зовут " . $sAndrey->getFullName() .
  " мне " . $sAndrey->getAge() . " лет<br>";
echo "У меня есть мама и папа. Маму зовут " . $sAndrey->getMother()->getFullName() . "<br>";
echo "Папу зовут " . $sAndrey->getFather()->getFullName() . "<br>";
echo "Привет!, меня зовут " . $dAnna->getFullName() .
  " мне " . $dAnna->getAge() . " лет<br>";
echo "У меня есть бабушка и дедушка мамины родители. Бабушку зовут " .
  $dAnna->getMother()->getMother()->getFullName() . "<br>";
echo "Дедушку зовут " . $dAnna->getMother()->getFather()->getFullName() . "<br>";
echo "Это еще не все у меня есть еще дедушка и бабушка папины родители. Бабушка " .
  $dAnna->getFather()->getMother()->getFullName() . "<br>";
echo "Дедушка " . $dAnna->getFather()->getFather()->getFullName();
