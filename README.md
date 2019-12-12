# Lafore-5-LinkList

import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;
import java.nio.Buffer;

class Algorithm {

    static class Link {

        public double data;
        public Link next;

        public Link(double newData) {
            data = newData;
            next = null;
        }

        public void displayLink() {
            System.out.println(data);
        }
    }

    static class LinkList {

        private Link first;

        public LinkList() {
            first = null;
        }

        public boolean isEmpty() {
            return(first == null);
        }

        public void insertFisrt(double data) {
            Link newLink = new Link(data);
            newLink.next = first;
            first = newLink;
        }

        public void deleteFirst() {
            if (!isEmpty())
                first = first.next;
        }

        public void displayList() {
            Link current = first;
            while(current != null) {
                current.displayLink();
                current = current.next;
            }
        }

        public Link find (double key) {
            Link current = first;
            while (current.data != key) {
                if (current.next == null)
                    return null;
                else
                    current = current.next;
            }
            return current;
        }

        public Link delete(double key) {
            Link current = first;
            Link previous = first;
            while (current.data != key) {
                if (current.next == null)
                    return null;
                else {
                    previous = current;
                    current = current.next;
                }
            }
            if (current == first)
                first = first.next;
            else
                previous.next = current.next;
            return current;
        }
    }

    public static void main(String[] arg) throws IOException {

        LinkList linkList = new LinkList();
        linkList.insertFisrt(50);
        linkList.insertFisrt(100);
        linkList.displayList();
        linkList.delete(100);
        linkList.displayList();

    }
}
