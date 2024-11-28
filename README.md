# Calculator-Project-for-PatikaDev-Web3
import Float "mo:base/Float";
import Iter "mo:base/Iter";

actor Calculator {
  var cell : Int = 0;

  public func add(x : Int) : async Int {
    cell += x;
    return cell;
  };

  public func sub(x : Int) : async Int {
    cell -= x;
    return cell;
  };

  public func mul(x : Int) : async Int {
    cell *= x;
    return cell;
  };

  public func div(x : Int) : async ?Int {
    if (x == 0) {
      return null;
    } else {
      cell /= x;
      return ?cell;
    };
  };

  public func power(exponent : Int) : async Int {
    var result : Int = 1;
    for (_ in Iter.range(1, exponent)) {
      result *= cell;
    };
    return result;
  };

  public func squareRoot() : async ?Float {
    if (cell < 0) {
      return null; // Negatif değerlerin karekökü yok
    } else {
      return ?Float.sqrt(Float.fromInt(cell));
    };
  };

  public func clearall() : async () {
    cell := 0;
  };
};
